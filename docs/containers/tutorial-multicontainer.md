---
title: Arbeiten mit mehreren Container mit Docker Compose
author: ghogen
description: Erfahren Sie, wie Sie mehrere Container mit Docker Compose verwenden.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 93f9d5ba8bd84341e1b314c1fabca07690114e39
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729287"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Tutorial: Erstellen einer App mit mehreren Containern mit Docker Compose

In diesem Tutorial erfahren Sie, wie Sie mehrere Container verwalten und zwischen ihnen kommunizieren können, wenn Sie Containertools in Visual Studio verwenden.  Für die Verwaltung mehrerer Container sind die *Containerorchestrierung* und ein Orchestrator wie Docker Compose, Kubernetes oder Service Fabric erforderlich. In diesem Tutorial wird Docker Compose verwendet. Docker Compose eignet sich bestens für das lokale Debuggen und Testen während des Entwicklungszyklus.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit den Workloads **Webentwicklung**, **Azure-Tools** oder der Workload **Plattformübergreifende .NET Core-Entwicklung** installiert
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierten Workloads für **Webentwicklung**, **Azure-Tools** und/oder **plattformübergreifende .NET Core-Entwicklung**
* [.NET Core 2.2-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/2.2) zur Entwicklung mit .NET Core 2.2
* [.NET Core 3-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/3.1) zur Entwicklung mit .NET Core 3.1
::: moniker-end

## <a name="create-a-web-application-project"></a>Erstellen eines Webanwendungsprojekts

Erstellen Sie in Visual Studio ein Projekt vom Typ **ASP.NET Core-Webanwendung** namens `WebFrontEnd`. Wählen Sie **Webanwendung** aus, um eine Webanwendung mit Razor-Seiten zu erstellen. 
  
::: moniker range="vs-2017"

Klicken Sie nicht auf **Docker-Unterstützung aktivieren**. Die Docker-Unterstützung fügen Sie erst später hinzu.

![Screenshot: Erstellen des Webprojekts](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Screenshot des Bildschirms zum Konfigurieren Ihres neuen Projekts für eine ASP.NET Core-Webanwendung, wobei die Felder „Projektname“ und „Projektmappenname“ auf „WebFrontEnd“ festgelegt sind.](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Klicken Sie nicht auf **Docker-Unterstützung aktivieren**. Die Docker-Unterstützung fügen Sie erst später hinzu.

![Screenshot des Bildschirms „Neue ASP.NET Core-Webanwendung erstellen“ mit ausgewählter Webanwendung. Die Option „Docker-Unterstützung aktivieren“ ist nicht aktiviert.](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Erstellen eines Web-API-Projekts

Fügen Sie ein Projekt zur gleichen Projektmappe hinzu, und nennen Sie es *MyWebAPI*. Wählen Sie **API** als Projekttyp aus, und deaktivieren Sie das Kontrollkästchen **Für HTTPS konfigurieren**. Bei diesem Entwurf wird SSL nur für die Kommunikation mit dem Client verwendet und nicht für die Kommunikation zwischen Containern in derselben Webanwendung. Nur `WebFrontEnd` erfordert HTTPS und der Code in den Beispielen geht davon aus, dass Sie dieses Kontrollkästchen deaktiviert haben. Im Allgemeinen werden die von Visual Studio verwendeten .NET-Entwicklerzertifikate nur für externe Anforderungen an Container unterstützt, nicht für Anforderungen zwischen Containern.

::: moniker range="vs-2017"
   ![Screenshot: Erstellen des Web-API-Projekts](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Screenshot: Erstellen des Web-API-Projekts](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Hinzufügen von Code zum Aufrufen der Web-API

1. Öffnen Sie die Datei *Index.cshtml.cs* im `WebFrontEnd`-Projekt, und ersetzen Sie die `OnGet`-Methode durch den folgenden Code.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Für tatsächlich verwendeten Code sollte `HttpClient` nicht nach jeder Anforderung gelöscht werden. Best Practices finden Sie unter [Verwenden von HttpClientFactory zur Implementierung robuster HTTP-Anforderungen](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Für .NET Core 3.1 in Visual Studio 2019 oder höher verwendet die Web-API-Vorlage eine WeatherForecast-API, also kommentieren Sie diese Zeile nicht aus. Kommentieren Sie stattdessen die Zeile für ASP.NET 2.x aus.

1. Fügen Sie der Datei *Index.cshtml* eine Zeile hinzu, um `ViewData["Message"]` so anzuzeigen, dass die Datei wie der folgende Code aussieht:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (Nur ASP.NET 2.x) Fügen Sie nun im Web-API-Projekt Code zum Controller „Values“ hinzu, um die von der API zurückgegebene Nachricht für den Aufruf anzupassen, den Sie über *webfrontend* hinzugefügt haben.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Mit .NET Core 3.1 ist dies nicht erforderlich, da Sie die bereits vorhandene WeatherForecast-API verwenden können. Allerdings müssen Sie den Aufruf von <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> in der `Configure`-Methode in *Startup.cs* auskommentieren, da dieser Code zum Aufrufen der Web-API HTTP verwendet, nicht HTTPS.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Klicken Sie im `WebFrontEnd`-Projekt auf **Hinzufügen > Unterstützung für Containerorchestrator**. Daraufhin wird das Dialogfeld **Docker-Supportoptionen** geöffnet.

1. Wählen Sie **Docker Compose** aus.

1. Wählen Sie Ihr Zielbetriebssystem aus, z. B. Linux.

   ![Screenshot: Auswahl des Zielbetriebssystems](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio erstellt eine *docker-compose.yml*- und eine *.dockerignore*-Datei im Knoten **docker-compose** der Projektmappe. Dieses Projekt wird in fetter Schrift aufgeführt, was angibt, dass es sich um das Startprojekt handelt.

   ![Screenshot: Projektmappen-Explorer mit dem Projekt „docker-compose“ hinzugefügt](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   Die Datei *docker-compose.yml* wird wie folgt angezeigt:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Die *.dockerignore*-Datei enthält Dateitypen und Erweiterungen, die Docker nicht im Container enthalten soll. Diese Daten stehen in der Regel in Verbindung mit der Entwicklungsumgebung und der Quellcodeverwaltung, nicht mit dem Teil der App bzw. des Diensts, den Sie entwickeln.

   Details zu den ausgeführten Befehlen finden Sie im Abschnitt **Containertools** des Ausgabebereichs.  Dort können Sie sehen, wie das Befehlszeilentool „docker-compose“ zum Konfigurieren und Erstellen der Runtimecontainer verwendet wird.

1. Klicken Sie im Web-API-Projekt erneut mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Hinzufügen** > **Unterstützung für Containerorchestrator** aus. Wählen Sie **Docker Compose** aus, und wählen Sie dann dasselbe Zielbetriebssystem aus wie zuvor.  

    > [!NOTE]
    > In diesem Schritt bietet Visual Studio an, eine Dockerfile zu erstellen. Wenn Sie dies in einem Projekt durchführen, das bereits über Docker-Unterstützung verfügt, werden Sie gefragt, ob Sie die vorhandene Dockerfile überschreiben möchten. Wenn Sie Änderungen an Ihrer Dockerfile vorgenommen haben, die Sie beibehalten möchten, wählen Sie „Nein“ aus.

    Visual Studio nimmt einige Änderungen an Ihrer Docker Compose-YML-Datei vor. Nun sind beide Dienste enthalten.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Führen Sie die Website jetzt lokal aus (F5 oder STRG + F5), um zu überprüfen, ob sie wie erwartet funktioniert. Wenn alles ordnungsgemäß mit der Version .NET Core 2.x konfiguriert ist, erhalten Sie die Meldung „Hello from webfrontend and webapi (with value 1).“ (Hallo vom webfrontend und der webapi (mit Wert 1)).  Mit .NET Core 3 werden die Daten der Wettervorhersage angezeigt.

   Das erste Projekt, das Sie beim Hinzufügen der Containerorchestrierung verwenden, ist so eingerichtet, dass es gestartet wird, wenn Sie die Ausführung oder das Debuggen starten. Sie können die Startaktion in den **Projekteigenschaften** des Projekts „docker-compose“ konfigurieren.  Klicken Sie mit der rechten Maustaste auf den Projektknoten „docker-compose“, um das Kontextmenü zu öffnen, und wählen Sie dann **Eigenschaften** aus, oder drücken Sie ALT + ENTER.  Im folgenden Screenshot werden die Eigenschaften gezeigt, die Sie für die Projektmappe verwenden sollten.  Sie können beispielsweise die geladene Seite ändern, indem Sie die Eigenschaft **Dienst-URL** anpassen.

   ![Screenshot: „docker-compose“-Projekteigenschaften](media/tutorial-multicontainer/launch-action.png)

   Hier sehen Sie, was beim Start (der Version .NET Core 2.x) angezeigt wird:

   ![Screenshot der ausgeführten Web-App](media/tutorial-multicontainer/webfrontend.png)

   Die Web-App für .NET 3.1 zeigt die Wetterdaten im JSON-Format an.

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich die Optionen zum Bereitstellen Ihrer [Container in Azure](/azure/containers) an.

## <a name="see-also"></a>Weitere Informationen
  
[Docker Compose](https://docs.docker.com/compose/)  
[Containertools](./index.yml)