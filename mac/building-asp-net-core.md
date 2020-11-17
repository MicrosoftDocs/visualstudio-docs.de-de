---
title: Erstellen von ASP.NET Core-Anwendungen
description: In diesem Artikel wird ausführlich gezeigt, wie Sie mit Visual Studio für Mac ASP.NET Core-Anwendungen erstellen und untersuchen.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 22dfa4a33005afd64be54828f3b49c45244779d2
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493503"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Erstellen von ASP.NET Core-Anwendungen in Visual Studio für Mac

ASP.NET Core ist ein plattformübergreifendes Open Source-Framework zum Erstellen moderner, cloudbasierter Anwendungen mit Internetverbindung, wie etwa Web-Apps und -Dienste, IoT-Apps und mobile Back-Ends. ASP.NET Core-Apps können unter [.NET Core-](https://www.microsoft.com/net/core/platform) oder .NET Framework-Runtimes ausgeführt werden. Es wurde entwickelt, um ein optimiertes Entwicklungsframework für Anwendungen bereitzustellen, die in der Cloud bereitgestellt oder vor Ort ausgeführt werden. Es besteht aus modularen Komponenten mit minimalem Overhead, sodass Sie Ihre Projektmappen flexibel erstellen können. Sie können Ihre ASP.NET Core-Apps plattformübergreifend unter Windows, macOS und Linux ausführen und entwickeln. ASP.NET Core ist auf [GitHub](https://github.com/aspnet/home) verfügbar.

In diesem Lab erstellen und untersuchen Sie eine ASP.NET Core-Anwendung mit Visual Studio für Mac.

## <a name="objectives"></a>Ziele

> [!div class="checklist"]
> * Erstellen einer ASP.NET Core-Web-App
> * Untersuchen von ASP.NET Core-Hosting, der Konfiguration und des Middlewaremodells
> * Debuggen einer ASP.NET Core-Web-App

## <a name="prerequisites"></a>Voraussetzungen

- [Visual Studio für Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Zielgruppe

Dieses Lab ist für Entwickler gedacht, die mit C# vertraut sind, tiefgreifende Kenntnisse sind jedoch nicht erforderlich.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Aufgabe 1: Erstellen einer neuen ASP.NET Core-Anwendung

1. Starten Sie **Visual Studio für Mac**.

2. Klicken Sie auf **Datei > Neue Projektmappe**.

3. Wählen Sie die Kategorie **.NET Core > App** und die Vorlage **ASP.NET Core-Web-App (C#)** aus. Klicken Sie auf **Weiter**.

    ![Screenshot, der zeigt, wie eine Webanwendungsvorlage für das neue Projekt ausgewählt wird.](media/netcore-image1.png)

4. Geben Sie den Namen **CoreLab** ein, und klicken Sie dann zum Erstellen des Projekts auf **Erstellen**. Es dauert einen Moment, bis der Vorgang abgeschlossen ist.

    ![Screenshot der Webanwendungskonfiguration, Hinzufügen eines Projektnamens.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Aufgabe 2: Erkunden der Projektmappe

1. Die Standardvorlage erstellt eine Projektmappe mit einem einzelnen ASP.NET Core-Projekt namens **CoreLab**. Erweitern Sie den Projektknoten, um seinen Inhalt anzuzeigen.

    ![Screenshot des ausgewählten Projektmappen-Projektknotens, um seinen Inhalt einschließlich Ordnern und Dateien anzuzeigen.](media/netcore-image3.png)

2. Dieses Projekt folgt dem MVC-Paradigma (Model-View-Controller, Modell-Ansicht-Controller), um die Aufgaben für Daten (Modelle), Präsentation (Ansichten) und Funktionen (Controller) klar voneinander zu trennen. Öffnen Sie im Ordner **Controller** die Datei **HomeController.cs**.

    ![Screenshot des Projektmappenprojekts mit einer ausgewählten C#-Klasse mit dem Namen „HomeController“.](media/netcore-image4.png)

3. Die **HomeController**-Klasse nach Konvention verarbeitet alle eingehenden Anforderungen, die mit **/Home** beginnen. Die **Index**-Methode verarbeitet Anforderungen an den Verzeichnisstamm (wie `http://site.com/Home`), und andere Methoden verarbeiten Anforderungen an ihren benannten Pfad basierend auf Konventionen. Beispielsweise verarbeitet **About()** Anforderungen an `http://site.com/Home/About`. Dies kann natürlich alles konfiguriert werden. Hervorzuheben ist, dass der **HomeController** der Standardcontroller in einem neuen Projekt ist, sodass Anforderungen an das Stammverzeichnis der Website (`http://site.com`) **Index()** von **HomeController** durchlaufen würden, genau wie Anforderungen an `http://site.com/Home` oder `http://site.com/Home/Index`.

    ![Screenshot einer C#-Klasse mit dem Namen „HomeController“.](media/netcore-image5.png)

4. Das Projekt enthält zudem einen Ordner **Ansichten**, der andere Ordner enthält, die den Controllern zugeordnet sind, sowie einen Ordner namens **Freigegeben**. Die CSHTML-Ansichtsdatei (eine Erweiterung von HTML) des Pfads **/Home/About** wäre z.B. **Views/Home/About.cshtml**. Öffnen Sie diese Datei.

    ![Screenshot des Projektmappenprojekts mit ausgewählter CSHTML-Datei mit dem Namen „About“.](media/netcore-image6.png)

5. Diese CSHTML-Datei verwendet die Razor-Syntax, um HTML auf der Grundlage einer Kombination von Standardtags und Inline-C# zu rendern. Weitere Informationen dazu finden Sie in der [Onlinedokumentation](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![Screenshot eines Teils einer CSHTML-Datei mit Razor-Syntax.](media/netcore-image7.png)

6. Diese Projektmappe enthält auch den Ordner **wwwroot**, der als Stammverzeichnis Ihrer Website dient. Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in den Pfaden einfügen, in denen sie sich bei der Bereitstellung der Website befinden sollen.

    ![Screenshot der Projektmappe mit ausgewähltem Stammordner „www“.](media/netcore-image8.png)

7. Es gibt auch verschiedene Konfigurationsdateien, mit denen Projekte einschließlich der Pakete und die Anwendung zur Laufzeit verwaltet werden können. Die [Standardkonfiguration](/aspnet/core/fundamentals/configuration) der Anwendung befindet sich z.B. in der Datei **appsettings.json**. Unterhalb der Datei „appsettings.json“ ist die Datei **appsettings.development.json** geschachtelt. Hier können Sie einige bzw. alle diese Einstellungen umgebungsbasiert außer Kraft setzen. Visual Studio für Mac schachtelt Dateien auf diese Weise mit derselben Logik wie Visual Studio für Windows, sodass Dateien, auf die Sie öfter zugreifen müssen, im Vordergrund stehen. 

    ![Screenshot mit einer Detailansicht, in der eine JSON-Datei ausgewählt ist.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Aufgabe 3: Verstehen, wie die Anwendung gehostet wird

1. Öffnen Sie im **Projektmappen-Explorer** die Datei **Program.cs**. Dies ist die Bootstrapperdatei, die Ihre Anwendung ausführt.

    ![Screenshot der Projektmappe, in der die C#-Quelldatei namens „Program“ ausgewählt ist.](media/netcore-image10.png)

2. Sie enthält zwar nur zwei Codezeilen, diese sind aber sehr wichtig. Schauen wir sie uns genauer an. Zunächst wird ein neuer **WebHostBuilder** erstellt. ASP.NET Core-Apps benötigen einen Host, in dem sie ausgeführt werden. Ein Host muss die **IWebHost**-Schnittstelle, die Sammlungen von Features und Diensten zur Verfügung stellt, und eine **Start**-Methode implementieren. Der Host wird in der Regel mit einer Instanz von **WebHostBuilder** erstellt, der eine **WebHost**-Instanz erstellt und zurückgibt. Der **WebHost** verweist auf den Server, der Anforderungen verarbeitet.

    ![Screenshot der C#-Main-Methode mit einer-Anweisung, die eine Variable namens „host“ mit dem Typ „WebHostBuilder“ initialisiert.](media/netcore-image11.png)

3. Auch wenn der **WebHostBuilder** für die Erstellung des Hosts zuständig ist, der den Bootstrap des Servers für die App durchführen soll, müssen Sie dafür einen Server bereitstellen, der **`IServer`** implementiert. Standardmäßig wird dafür **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)** verwendet, ein plattformübergreifender Webserver für ASP.NET Core, der auf der plattformübergreifenden asynchronen E/A-Bibliothek **libuv** basiert.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Hostvariablen, die den Server mit der UseKestrel-Methode festlegt.](media/netcore-image12.png)

4. Als Nächstes wird das Inhaltsstammverzeichnis des Servers festgelegt. Dadurch wird festgelegt, wo nach Inhaltsdateien wie MVC-Ansichtsdateien gesucht wird. Das standardmäßige Inhaltsstammverzeichnis ist der Ordner, über den die Anwendung ausgeführt wird.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Hostvariablen, die den Inhaltsstamm für den Server mit der UseContentRoot-Methode festlegt.](media/netcore-image13.png)

5. Wenn die Anwendung mit dem Webserver für Internetinformationsdienste (Internet Information Services, IIS) zusammenarbeiten muss, sollte die **UseIISIntegration**-Methode als Teil des Hostaufbaus aufgerufen werden. Damit wird jedoch kein Server konfiguriert, wie es mit **UseKestrel** der Fall ist. Um IIS mit ASP.NET Core verwenden zu können, müssen Sie sowohl **UseKestrel** als auch **UseIISIntegration** angeben. **Kestrel** ist so konzipiert, dass es hinter einem Proxy ausgeführt wird und sollte nicht direkt auf das Internet ausgerichtet sein. **UseIISIntegration** spezifiziert IIS als Reverseproxyserver. Dies ist jedoch nur relevant, wenn es auf Computern mit IIS ausgeführt wird. Wenn Sie Ihre Anwendung in Windows bereitstellen, belassen Sie es dabei. Dies hat keine negativen Auswirkungen.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Hostvariablen, die den Reverseproxyserver mit der UseIISIntegration-Methode festlegt.](media/netcore-image14.png)

6. Es ist übersichtlicher, das Laden von Einstellungen vom Bootstrapping der Anwendung zu trennen. Um dies zu erleichtern, wird **UseStartup** aufgerufen, um anzugeben, dass die **Startup**-Klasse für das Laden von Einstellungen und anderen Startaufgaben, wie z.B. das Einfügen von Middleware in die HTTP-Pipeline, aufgerufen werden soll. Sie müssen **UseStartup** möglicherweise mehrfach mit der Annahme aufrufen, dass jeder einzelne Aufruf die vorherigen Einstellungen bei Bedarf überschreibt.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Hostvariablen, die die Startklasse mit der UseStartup-Methode festlegt.](media/netcore-image15.png)

7. Der letzte Schritt beim Erstellen des **IWebHost** ist das Aufrufen von **Build**.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Hostvariablen mit der Build-Methode.](media/netcore-image16.png)

8. Obwohl **IWebHost**-Klassen erforderlich sind, um die nicht blockierenden **Start**-Methode zu implementieren, verfügen ASP.NET-Core-Projekte über eine Erweiterungsmethode namens **Run**, die **Start** mit Blockierungscode umschließt, sodass Sie nicht manuell verhindern müssen, dass die Methode sofort beendet wird.

    ![Screenshot der C#-Main-Methode mit hervorgehobener Anweisung host dot Run.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Aufgabe 4: Ausführen und Debuggen der Anwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten **CoreLab**, und wählen Sie **Optionen** aus.

    ![Screenshot des Kontextmenüs für die CoreLab-Projektmappe mit hervorgehobenen „Optionen“.](media/netcore-image18.png)

2. Das Dialogfeld **Projektoptionen** enthält alles, was Sie benötigen, um anzupassen, wie die Anwendung erstellt und ausgeführt wird. Wählen Sie im linken Bereich den Knoten **Ausführen > Konfigurationen > Standard** aus.

3. Aktivieren Sie das Kontrollkästchen **Auf externer Konsole ausführen**, und deaktivieren Sie **Konsolenausgabe anhalten**. Normalerweise ist die Konsole der selbstgehosteten Anwendung nicht sichtbar, sondern protokolliert ihre Ergebnisse im **Ausgabefenster**. Für die Zwecke dieses Labs werden wir dies in einem separaten Fenster darstellen, obwohl das während der normalen Entwicklung nicht erforderlich ist.

4. Klicken Sie auf **OK**.

    ![Screenshot der Registerkarte „Run Configuration General“ (Laufzeitkonfiguration allgemein) mit ausgewählter Option „Run“ (Ausführen) für externe Konsole und nicht ausgewählter Option „Pause“ (Anhalten) für die Konsolenausgabe.](media/netcore-image19.png)

5. Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen. Alternativ können Sie **Ausführen > Debuggen starten** auswählen.

6. Visual Studio für Mac öffnet zwei Fenster. Das erste ist ein Konsolenfenster mit einem Einblick in die selbst gehostete Serveranwendung.

    ![Screenshot des Konsolenfensters für die selbstgehostete Serveranwendung.](media/netcore-image20.png)

7. Das zweite ist ein typisches Browserfenster, um die Website zu testen. Der Browser weiß, dass diese Anwendung überall gehostet werden kann. Klicken Sie auf **Info**, um zu dieser Seite navigieren.

    ![Screenshot eines Browserfensters zum Testen der Website mit hervorgehobener Option „About“ (Info).](media/netcore-image21.png)

8. Unter anderem rendert die Infoseite Text, der im Controller festgelegt ist.

    ![Screenshot mit dem Ergebnis der Auswahl der Option „About“ (Info): Seite „About“.](media/netcore-image22.png)

9. Lassen Sie beide Fenster geöffnet, und kehren Sie zu Visual Studio für Mac zurück. Öffnen Sie **Controllers/HomeController.cs**, wenn es nicht bereits geöffnet ist.

    ![Screenshot der Projektmappe mit erneut ausgewählter C#-Klasse „HomeController“.](media/netcore-image23.png)

10. Legen Sie in der ersten Zeile der Methode **About** einen Haltepunkt fest. Klicken Sie dazu auf den Rand, oder setzen Sie den Cursor auf die Zeile, und drücken Sie **F9**. Diese Zeile legt einige Daten der Auflistung **ViewData** fest, die auf der CSHTML-Seite unter **Views/Home/About.cshtml** gerendert wird.

    ![Screenshot der About-Methode mit einem festgelegten Breakpoint.](media/netcore-image24.png)

11. Kehren Sie zum Browser zurück, und aktualisieren Sie die Infoseite. Dadurch wird der Breakpoint in Visual Studio für Mac ausgelöst.

12. Bewegen Sie die Maus über den Member **ViewData**, um dessen Daten anzuzeigen. Sie können auch seine untergeordneten Member erweitern, um die geschachtelten Daten anzuzeigen.

    ![Screenshot, der einen Breakpoint mit seinen erweiterten Daten zeigt.](media/netcore-image25.png)

13. Entfernen Sie den Anwendungshaltepunkt mit derselben Methode, mit der Sie ihn hinzugefügt haben.

14. Öffnen Sie **Views/Home/About.cshtml**.

15. Ändern Sie den Text **additional** in **changed**, und speichern Sie die Datei.

    ![Screenshot der CSHTML-Datei namens „About“ mit einer Textänderung.](media/netcore-image26.png)

16. Drücken Sie auf **Weiter**, um die Ausführung fortzusetzen.

    ![Screenshot des Visual Studio-Fensters mit hervorgehobener Schaltfläche „Continue“ (Weiter).](media/netcore-image27.png)

17. Kehren Sie zum Browserfenster zurück, um den aktualisierten Text zu prüfen. Diese Änderung ist jederzeit möglich und erfordert nicht unbedingt einen Debuggerbreakpoint. Aktualisieren Sie den Browser, wenn die Änderung nicht sofort angezeigt wird.

    ![Screenshot der Seite „About“ (Info) mit geändertem Text.](media/netcore-image28.png)

18. Schließen Sie das Browsertestfenster und die Anwendungskonsole. Dadurch wird auch das Debuggen beendet.

## <a name="task-5-application-startup-configuration"></a>Aufgabe 5: Konfiguration des Anwendungsstarts

1. Öffnen Sie im **Projektmappen-Explorer** die Datei **Startup.cs**. Sie werden vielleicht zunächst einige rote Wellenlinien bemerken, da NuGet-Pakete im Hintergrund wiederhergestellt werden und der Roslyn-Compiler eine vollständige Darstellung der Projektabhängigkeiten erstellt.

    ![Screenshot der Projektmappe mit ausgewählter Datei „Startup“ der C#-Klasse.](media/netcore-image29.png)

2. Suchen Sie die **Startup**-Methode. Dieser Abschnitt definiert die Anfangskonfiguration für die Anwendung und ist dicht gepackt. Im Folgenden wird sie zunächst aufgeschlüsselt.

    ![Screenshot der Startup-Methode der Startup-Klasse.](media/netcore-image30.png)

3. Die Methode beginnt mit der Initialisierung eines **ConfigurationBuilder** und dem Festlegen des Basispfades.

    ![Screenshot der Startup-Methode mit einer Anweisung zum Initialisieren einer Variablen namens „builder“ mit dem Typ „ConfigurationBuilder“.](media/netcore-image31.png)

4. Als Nächstes wird die erforderliche Datei **appsettings.json** geladen.

    ![Screenshot der Startup-Methode mit der builder-Variablen, die die AddJsonFile-Methode zum Hinzufügen der JSON-Datei namens „appsettings“ verwendet.](media/netcore-image32.png)

5. Danach wird versucht, eine umgebungsspezifische Datei **appsettings.json** zu laden, die bestehende Einstellungen überschreibt. Dies ist beispielsweise eine bereitgestellte Datei **appsettings.Development.json**, die für diese spezifische Umgebung verwendet wird. Weitere Informationen zur Konfiguration in ASP.NET Core finden Sie in der [Dokumentation](/aspnet/core/fundamentals/configuration).

    ![Screenshot der Startup-Methode mit der builder-Variablen, die die AddJsonFile-Methode zum Hinzufügen einer umgebungsspezifischen JSON-Datei namens „appsettings“ verwendet.](media/netcore-image34.png)

6. Abschließend werden die Umgebungsvariablen zum Konfigurationsbuilder hinzugefügt, und die Konfiguration wird erstellt und zur Verwendung bereitgestellt.

    ![Screenshot der Startup-Methode mit der builder-Variablen zum Hinzufügen von Umgebungsvariablen und Verwenden der Build-Methode zum Erstellen der Konfiguration.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Aufgabe 6: Einfügen von Middleware für die Anwendung

1. Suchen Sie die **Configure**-Methode in der **Startup**-Klasse. Hier ist die gesamte Middleware konfiguriert, sodass sie in die HTTP-Pipeline eingefügt und zur Bearbeitung jeder Anforderung an den Server verwendet werden kann. Diese Methode wird zwar nur einmal aufgerufen, aber der Inhalt der Methoden (z.B. **UseStaticFiles**) kann bei jeder Anforderung ausgeführt werden.

    ![Screenshot der Configure-Methode in der Startup-Klasse.](media/netcore-image36.png)

2. Sie können auch zusätzliche Middleware hinzufügen, die als Teil der Pipeline ausgeführt werden soll. Fügen Sie den folgenden Code nach **app.UseStaticFiles** hinzu, um automatisch einen **X-Test**-Header zu jeder ausgehenden Antwort hinzuzufügen. IntelliSense unterstützt Sie während der Eingabe bei der Vervollständigung des Codes.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.

4. Wir können den Browser zum Überprüfen der Header verwenden, um sicherzustellen, dass sie hinzugefügt wurden. Die folgenden Anweisungen gelten für Safari, aber Sie können dieselben Schritte auch in [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) oder [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console) ausführen.

5. Wenn der Browser die Website geladen hat, wählen Sie **Safari > Voreinstellungen** aus.

6. Aktivieren Sie auf der Registerkarte **Erweitert** die Option **Menü „Entwickler“ in der Menüleiste anzeigen**, und schließen Sie das Dialogfeld.

    ![Screenshot des Bereichs „Advanced“ (Erweitert) im Dialogfeld „Safari Preferences“ (Safari-Einstellungen) mit ausgewählter Option „Show Develop menu in menu bar“ (Menü „Entwickler“ in der Menüleiste anzeigen).](media/netcore-image37.png)

7. Wählen Sie **Entwickeln > Seitenressourcen anzeigen**.

8. Aktualisieren Sie das Browserfenster, damit die neu geöffneten Entwicklertools den Datenverkehr und den Inhalt verfolgen und analysieren können.

9. Die vom Server gerenderte HTML-Seite „localhost“ ist das standardmäßig ausgewählte Element.

    ![Screenshot der hervorgehobenen HTML-Seite „localhost“.](media/netcore-image38.png)

10. Erweitern Sie die **Randleiste „Details“**.

    ![Screenshot mit hervorgehobenem Steuerelement zum Erweitern der Randleiste „Details“.](media/netcore-image39.png)

11. Scrollen Sie zum unteren Rand der Seitenleiste, um den Antwortheader zu sehen, der zuvor im Code hinzugefügt wurde.

    ![Screenshot mit hervorgehobenem Antwortheader namens XTest mit dem Wert „Test value“ (Testwert).](media/netcore-image40.png)

12. Schließen Sie das Browserfenster und die Konsole, wenn Sie mit dem Ergebnis zufrieden sind.

## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie mehr über die ersten Schritte beim Entwickeln von ASP.NET Core-Apps mithilfe von Visual Studio für Mac erfahren. Wenn Sie sich die Entwicklung einer umfassenderen Filmdatenbankanwendung ansehen möchten, schauen Sie sich das Tutorial [Erste Schritte mit ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) an.
