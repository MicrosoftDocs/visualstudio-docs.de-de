---
title: Erste Schritte mit ASP.NET Core
description: In diesem Artikel erfahren Sie mehr über die ersten Schritte mit ASP.NET in Visual Studio für Mac, insbesondere über die Installation und das Erstellen eines neuen Projekts.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 2e921ac1e9c85216bebf1626e1454b9fb764f129
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85938938"
---
# <a name="getting-started-with-aspnet-core"></a>Erste Schritte mit ASP.NET Core

 Visual Studio für Mac erleichtert die Entwicklung des Diensts Ihrer App durch Unterstützung der aktuellen ASP.NET Core Web-Entwicklungsplattform. ASP.NET Core wird unter .NET Core ausgeführt, der aktuellen Version von .NET Framework und der zugehörigen Runtime. Die Anwendung wurde für schnelle Leistung optimiert, für kleine Installationsgrößen konzipiert und für die Ausführung unter Linux und macOS sowie Windows überarbeitet.

## <a name="installing-net-core"></a>Installieren von .NET Core

.NET Core 1.1 wird automatisch mit der Installation von Visual Studio für Mac installiert.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Erstellen einer ASP.NET Core-App in Visual Studio für Mac

Öffnen Sie Visual Studio für Mac. Klicken Sie auf der Homepage auf**Neues Projekt...** .

![Dialogfeld "Neues Projekt"](media/asp-net-core-image1.png)

Dies öffnet das Dialogfeld „Neues Projekt“, über das Sie eine Vorlage zum Erstellen Ihrer Anwendung auswählen können.

Es gibt einige Projekte, die eine vorgefertigte Vorlage zum Erstellen einer ASP.NET Core-Anwendung haben. Diese lauten wie folgt:

- **.NET Core > Leere ASP.NET Core-Webanwendung**
- **.NET Core > ASP.NET Core-Webanwendung**
- **.NET Core > ASP.NET Core Web-API**
- **Mehrere Plattformen > App > Verbundende App**

![ASP.NET-Projektoptionen](media/asp-net-core-image11.png)

Klicken Sie auf die **leere ASP.NET Core-Webanwendung** und dann auf **Weiter**. Benennen Sie das Projekt, und klicken Sie auf **Erstellen**. Dadurch wird eine neue ASP.NET Core-Anwendung erstellt, die in etwa so aussehen sollte wie auf folgendem Bild:

![Ansicht „Neue leere ASP.NET Core-Anwendung“](media/asp-net-core-image4.png)

Mit „Leere ASP.NET Core-Webanwendung“ wird eine neue Webanwendung mit zwei Standarddateien erstellt: **Program.cs** und **Startup.cs**, die unten weiter erläutert werden. Außerdem wird der Ordner „Abhängigkeiten“ erstellt, der die NuGet-Paketabhängigkeiten Ihres Projekts enthält, z. B. ASP.NET Core, das .NET Core-Framework und die Ziele von MSBuild, die das Projekt erstellen:

![Anzeige des Projektmappenpads mit Abhängigkeiten](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Öffnen sie die Datei **program.cs** in Ihrem Projekt, und schauen Sie sich diese an. Beachten Sie, dass zwei Dinge in der `Main`-Methode passieren – der Eingang Ihrer Anwendung:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```

Eine ASP.NET Core-Anwendung erstellt in ihrer Hauptmethode einen Webserver, indem sie einen Host über eine Instanz von [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) konfiguriert und startet. Dieser Generator bietet Möglichkeiten zur Konfiguration des Hosts. In der Vorlagenanwendung werden die folgenden Konfigurationen verwendet:

* `UseKestrel`: Gibt an, dass der Kestrel-Server von der Anwendung verwendet wird.
* `UseContentRoot(Directory.GetCurrentDirectory())`: Verwendet den Stammordner des Webprojekts als Inhaltsstamm der Anwendung, wenn die Anwendung aus diesem Ordner gestartet wird.
* `.UseIISIntegration()`: Gibt an, dass die Anwendung mit IIS funktionieren soll. Um IIS mit ASP.NET Core verwenden zu können, muss sowohl `UseKestrel` als auch `UseIISIntegration` festgelegt sein.
* `.UseStartup<Startup>()`: Gibt die Startup-Klasse an.

  Die Methoden zum Erstellen und Ausführen erstellen den IWebHost, der die App hostet und startet, während er auf eingehende HTTP-Anforderungen lauscht.

### <a name="startupcs"></a>Startup.cs

Die Startup-Klasse für Ihre Anwendung wird in der `UseStartup()`-Methode im `WebHostBuilder` festgelegt. In dieser Klasse legen Sie die Pipeline fest, die Anforderungen verarbeitet. Darüber hinaus können Sie hier jeden Dienst konfigurieren.

Öffnen sie die Datei **startup.cs** in Ihrem Projekt, und schauen Sie sich diese an.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

Diese Startup-Klasse muss sich immer an folgende Regeln halten:

- Sie muss immer öffentlich sein.
- Sie muss die beiden öffentlichen Methoden `ConfigureServices` und `Configure` enthalten

Die `ConfigureServices`-Methode definiert die Dienste, die von Ihrer Anwendung verwendet werden.

Mit der `Configure`-Methode können Sie Ihre Anforderungspipeline mit [Middleware](/aspnet/core/fundamentals/middleware) erstellen. Dabei handelt es sich um Komponenten, die in einer ASP.NET-Anwendungspipeline verwendet werden, um Anforderungen und Reaktionen zu behandeln. Die HTTP-Pipeline besteht aus Anforderungsdelegaten, die nacheinander aufgerufen werden. Jeder Delegat kann die Anforderung entweder selbst behandeln oder sie an den nächsten Delegaten übergeben.

Sie können Delegate mit den Methoden `Run`, `Map` und `Use` in `IApplicationBuilder` konfigurieren, aber die `Run`-Methode ruft niemals den nächsten Delegaten auf und sollte immer am Ende Ihrer Pipeline verwendet werden.

Die `Configure`-Methode der vorgefertigten Vorlage wurde speziell für einige bestimmte Aktionen entwickelt. Zunächst konfiguriert sie eine Seite zur Behandlung von Ausnahmen, die während der Entwicklung verwendet werden kann. Danach sendet sie eine Antwort an die anfragende Webseite, die einfach „Hello World“ enthält.

Dieses einfache „Hello World“-Projekt kann nun ausgeführt werden, ohne das zusätzlicher Code hinzugefügt werden muss. Um die App auszuführen und in Ihrem Browser anzuzeigen, klicken Sie auf die Schaltfläche „Wiedergabe“ (Dreieck) in der Symbolleiste:

![Ausführen der App](media/asp-net-core-image5.png)

Visual Studio für Mac verwendet einen zufälligen Port, um Ihr Webprojekt zu starten. Um herauszufinden um welche Port es sich dabei handelt, öffnen Sie die Anwendungsausgabe, die sich unter **Ansicht > Pads** befindet. Dort sollten Sie eine Ausgabe wie die folgende sehen:

![Anwendungsausgabe mit lauschendem Port](media/asp-net-core-image6.png)

Öffnen Sie den Browser Ihrer Wahl, und geben Sie `http://localhost:5000/` ein. Ersetzen Sie dabei `5000` durch die Visual Studio-Ausgabe in der Anwendungsausgabe. Der Text `Hello World!` sollte angezeigt werden:

![Browser mit Text](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Hinzufügen eines Controllers

ASP.NET Core-Apps verwenden das Entwurfsmuster von Model-View-Controller (MVC), um eine logische Trennung zwischen den Verantwortlichkeiten der verschiedenen Teile der Anwendung zu gewährleisten. MVC besteht aus den folgenden Elementen:

- **Model**: Eine Klasse, die die Daten der App darstellt.
- **Ansicht**: Zeigt die Benutzeroberfläche der App an (wobei es sich häufig um die Modelldaten handelt).
- **Controller**: Eine Klasse, die Browseranforderungen verarbeitet und auf Benutzereingaben und -interaktionen reagiert.

Weitere Informationen zum Verwenden von MVC finden Sie im Handbuch [Overview of ASP.NET Core MVC (Überblick über ASP.NET Core MVC)](/aspnet/core/mvc/overview).

Um einen Controller hinzuzufügen, führen Sie Folgendes durch:

1. Klicken Sie mit der rechten Maustaste auf den Projektnamen und dann auf **Neues Element hinzufügen**. Klicken Sie auf **Allgemein > Leere Klasse**, und geben Sie einen Controllernamen ein:

    ![Dialogfeld „Neue Datei“](media/asp-net-core-image8.png)

2. Fügen Sie dem neuen Controller den folgenden Code hinzu:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Fügen Sie die `Microsoft.AspNetCore.Mvc`-Abhängigkeit zu dem neuen Projekt hinzu, indem Sie mit der rechten Maustaste auf den Ordner **Abhängigkeiten** und dann auf **Paket hinzufügen...** klicken.

4. Verwenden Sie das Suchfeld, um die NuGet-Bibliothek nach `Microsoft.AspNetCore.Mvc` zu durchsuchen, und klicken Sie dann auf **Paket hinzufügen**. Die Installation kann einige Minuten in Anspruch nehmen, und Sie werden möglicherweise aufgefordert, verschiedene Lizenzen für die erforderlichen Abhängigkeiten zu akzeptieren:

    ![Hinzufügen eines NuGet-Pakets](media/asp-net-core-image9.png)

5. Entfernen Sie in der Startup-Klasse den `app.Run`-Lambdaausdruck, und legen Sie die URL-Routinglogik auf Folgendes fest, die von MVC verwendet wird, um zu bestimmen, welcher Code aufgerufen werden soll:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Achten Sie darauf, dass Sie den `app.Run`-Lambdaausdruck entfernen, da dieser die Routinglogik außer Kraft setzt.

    MVC verwendet das folgende Format, um zu bestimmen, welche Code ausgeführt werden soll:

    `/[Controller]/[ActionName]/[Parameters]`

    Wenn Sie den oben stehenden Codeausschnitte hinzufügen, sagen Sie der App damit, den `HelloWorld`-Controller und die `Index`-Aktionsmethode als Standard zu verwenden.

6. Fügen Sie der `ConfigureServices`-Methode den `services.AddMvc();`-Aufruf hinzu, wie unten gezeigt:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Sie können auch Parameterinformationen von der URL an den Controller übergeben.

7. Fügen Sie eine weitere Methode zu HelloWorldController hinzu, wie unten gezeigt:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Wenn Sie jetzt die App ausführen, sollte Sie automatisch Ihren Browser öffnen:

    ![Ausführen der App im Browser](media/asp-net-core-image13.png)

9. Wenn Sie zu `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` navigieren und `xxxx` durch den korrekten Port ersetzen, sollte Folgendes angezeigt werden.

    ![Ausführen der App im Browser mit Argumenten.](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie .NET Core manuell unter Mac OS 10.11 (El Capitan) installieren müssen, führen Sie Folgendes durch:

1. Bevor Sie mit der Installation von .NET Core beginnen, achten Sie darauf, dass Sie alle Betriebssystemupdates auf die aktuelle stabile Version durchgeführt haben. Dies können Sie überprüfen, indem Sie zur App Store-Anwendung navigieren und auf die Registerkarte Updates klicken.

2. Folgen Sie den Schritten auf der [.NET Core-Website](https://www.microsoft.com/net/core#macos).

Achten Sie darauf, dass Sie alle vier Schritte erfolgreich abschließen, um sicherzustellen, dass .NET Core ordnungsgemäß installiert wurde.

## <a name="summary"></a>Zusammenfassung

Dieses Handbuch hat Sie in ASP.NET Core eingeführt. Nun wissen Sie, was ASP.NET Core ist und wofür und wie Sie es in Visual Studio für Mac verwenden können.
Weiter Informationen zu weiteren Schritten finden Sie in den folgenden Handbüchern:
- Dokumentation zu [ASP.NET Core](/aspnet/core/)
- [Creating Backend Services for Native Mobile Applications (Erstellen von Back-End-Diensten für native mobile Anwendungen)](/aspnet/core/mobile/native-mobile-backend), wo Sie erfahren, wie Sie einen REST-Dienst mit ASP.NET Core für eine Xamarin.Forms-App erstellen können.
- [Praktische Übung zu ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]