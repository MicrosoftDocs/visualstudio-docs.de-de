---
title: Multicontainer-App mit Docker Compose
description: Erfahren Sie, wie Sie mehr als einen Container verwalten und zwischen ihnen in Visual Studio für Mac kommunizieren können.
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: f2c5154e2f35c57b46817c36ea669c6a9d0f5797
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493542"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Erstellen einer App mit mehreren Containern mit Docker Compose

In diesem Tutorial erfahren Sie, wie Sie mehrere Container verwalten und zwischen ihnen kommunizieren können, wenn Sie Docker Compose in Visual Studio für Mac verwenden.

## <a name="prerequisites"></a>Voraussetzungen

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio für Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Erstellen einer ASP.NET Core-Webanwendung und Hinzufügen von Docker-Unterstützung

1. Erstellen Sie eine neue Projektmappe, indem Sie zu **Datei > Neue Projektmappe** wechseln.
1. Wählen Sie unter **Web und Konsole > App** die Vorlage **Webanwendung** aus: ![Erstellen einer neuen ASP.NET-Anwendung](media/docker-quickstart-1.png)
1. Wählen Sie das Zielframework aus. In diesem Beispiel verwenden wir .NET Core 3.1: ![Festlegen des Zielframeworks](media/docker-quickstart-2.png)
1. Geben Sie die Projektdetails, z.B. den Projektnamen (_DockerDemoFrontEnd_ in diesem Beispiel) und einen Projektmappennamen (_DockerDemo_) ein. Das erstellte Projekt enthält alle Grundinformationen, die Sie für Aufbau und Betrieb einer ASP.NET Core-Website benötigen.
1. Klicken Sie im Projektmappenfenster mit der rechten Maustaste auf das Projekt „DockerDemoFrontEnd“, und wählen Sie **Hinzufügen > Docker-Unterstützung hinzufügen** aus: ![Hinzufügen von Docker-Unterstützung](media/docker-quickstart-3.png)

Visual Studio für Mac fügt Ihrer Projektmappe automatisch ein neues Projekt namens **docker-compose** und dem bestehenden Projekt eine **Dockerfile** hinzu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Erstellen einer ASP.NET Core-Web-API und Hinzufügen von Docker-Unterstützung

Als Nächstes erstellen wir ein zweites Projekt, das als unsere Back-End-API fungiert. Die Vorlage **.NET Core-API** enthält einen Controller, der es uns ermöglicht, RESTful-Anforderungen zu verarbeiten.

1. Fügen Sie der bestehenden Projektmappe ein neues Projekt hinzu, indem Sie mit der rechten Maustaste auf die Projektmappe klicken und **Hinzufügen > Neues Projekt hinzufügen** wählen.
1. Wählen Sie unter **Web und Konsole > App** die Vorlage **API** aus.
1. Wählen Sie das Zielframework aus. In diesem Beispiel verwenden wir .NET Core 3.1.
1. Geben Sie die Projektdetails ein, z. B. den Projektnamen (_MyWebAPI_ in diesem Beispiel).
1. Klicken Sie nach der Erstellung im Projektmappenfenster mit der rechten Maustaste auf das Projekt „MyWebAPI“, und wählen dann Sie **Hinzufügen > Docker-Unterstützung hinzufügen** aus.

Die Datei **docker-compose.yml** im Projekt **docker-compose** wird automatisch so aktualisiert, dass sie neben dem bestehenden Web-App-Projekt auch das API-Projekt enthält. Wenn wir das **docker-compose**-Projekt erstellen und ausführen, wird jedes dieser Projekte in einem eigenen Docker-Container bereitgestellt.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrieren der beiden Container

Wir haben nun zwei ASP.NET-Projekte in unserer Projektmappe, die beide mit Docker-Unterstützung konfiguriert sind. Als Nächstes müssen wir Code hinzufügen.

1. Öffnen Sie die Datei *Pages/Index.cshtml.cs* im `DockerDemoFrontEnd`-Projekt, und ersetzen Sie die `OnGet`-Methode durch den folgenden Code:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Im Produktionscode sollte `HttpClient` nicht nach jeder Anforderung verworfen werden. Best Practices finden Sie unter [Verwenden von HttpClientFactory zur Implementierung robuster HTTP-Anforderungen](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. Fügen Sie der Datei *Index.cshtml* eine Zeile hinzu, um `ViewData["Message"]` so anzuzeigen, dass die Datei wie der folgende Code aussieht:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. Kommentieren Sie sowohl im Front-End- als auch im Web-API-Projekt den Aufruf von [Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection](/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) in der `Configure`-Methode in *Startup.cs* aus, weil dieser Beispielcode für den Aufruf der Web-API HTTP verwendet, nicht HTTPS.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Legen Sie das Projekt `docker-compose` als Startprojekt fest, und wechseln Sie zu **Ausführen > Debuggen starten**. Wenn alles ordnungsgemäß konfiguriert ist, erhalten Sie die Meldung "Hello from webfrontend and webapi (with value 1).":

![Ausgeführte Docker-Lösung mit mehreren Containern](media/docker-multicontainer-debug.png)