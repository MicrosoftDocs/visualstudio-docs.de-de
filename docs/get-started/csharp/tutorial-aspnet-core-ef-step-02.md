---
title: 'Schritt 2: Erstellen Ihrer ersten ASP.NET Core-Web-App'
description: Erstellen Sie Ihre erste ASP.NET Core-Web-App mithilfe dieses Videotutorials und den exemplarischen Anweisungen.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e560d9028a7c2044964f5a2ec54e8daefea26372
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922820"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Schritt 2: Erstellen Ihrer ersten ASP.NET Core-Web-App

Erstellen Sie Ihre erste ASP.NET Core-Web-App mithilfe dieses Videotutorials und den exemplarischen Anweisungen.

_Sehen Sie sich dieses Video an, und folgen Sie den einzelnen Schritten, um Ihre erste ASP.NET Core-App zu erstellen._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Starten von Visual Studio 2019 und Erstellen eines neuen Projekts

Starten Sie Visual Studio 2019, und klicken Sie auf **Neues Projekt erstellen**. Wählen Sie **ASP.NET Core-Webanwendung** aus. Wählen Sie die Vorlage **Webanwendung** aus, und behalten Sie den Standardprojektnamen sowie den Standardspeicherort bei. Wählen Sie in der Dropdownliste mit der ASP.Net Core Version **ASP.Net Core 2.1** oder **ASP.Net Core 2.2** aus. Klicken Sie auf **Erstellen**. Ausführlichere Anweisungen finden Sie im [vorherigen Video dieser Tutorialreihe](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 – Auswählen von ASP.NET Core-Projektoptionen](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Stellen Sie sicher, dass Sie ASP.NET Core 2.1 oder ASP.NET Core 2.2 auswählen. Dieses Tutorial ist nicht kompatibel mit ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Untersuchen des neuen Projekts

Sie können die Inhalte des neuen Projekts im Fenster „Projektmappen-Explorer“ rechts anzeigen. Diese Inhalte werden im Folgenden beschrieben.

![ASP.NET Core-Projekt in Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Der Ordner *wwwroot* enthält statische Dateien, auf die über die Webanwendung öffentlich zugegriffen werden kann. In der Regel sind Stylesheets, clientseitige Skriptdateien und Bilder enthalten.

### <a name="pages"></a>Seiten

Der Ordner *Pages* enthält die Razor-Seiten der Website. Die Standardvorlage stellt mehrere Seiten einschließlich der Seite *Index.cshtml* bereit. Dabei handelt es sich um die Startseite der Anwendung sowie die Seiten „Info“, „Kontakt“ usw.

### <a name="appsettingsjson"></a>appsettings.json

Diese Datei enthält die Konfigurationseinstellungen für die Website im JSON-Format.

### <a name="programcs"></a>Program.cs

Diese Datei dient als Einstiegspunkt für die Anwendung. Wenn die App ausgeführt wird, wird als Erstes die Main-Methode ausgeführt. Diese ist für das Erstellen des Webhosts verantwortlich, der die Anwendung enthält.

### <a name="startupcs"></a>Startup.cs

Der in *Program.cs* erstellte Webhost verweist auf die Startup-Klasse und ruft dessen Methoden auf, um die Anwendung zu konfigurieren. Die ConfigureServices-Methode ist für das Einrichten jeglicher Dienste verantwortlich, die die App verwendet. Die `Configure`-Methode richtet die HTTP-Anforderungspipeline der App ein. Jede Anforderung durchläuft diese Pipeline und interagiert mit der *Middleware*.

### <a name="indexcshtml"></a>Index.cshtml

Die Startseite der Website umfasst HTML-Markup und serverseitigen Razor-Code. Razor wird zum Angeben des Seitenmodells `IndexModel` verwendet, das sich in der zugehörigen Datei *Index.cshtml.cs* befindet. Außerdem wird der Seitentitel durch Festlegen eines Werts in ViewData festgelegt. Dieser ViewData-Wert wird in der Datei *\_Layout.cshtml* gelesen, die sich im Ordner „Shared“ innerhalb des Ordners „Pages“ befindet. Die Layoutdatei wird von vielen Razor-Seiten genutzt und stellt das gängige Aussehen und Verhalten der Anwendung bereit. Der Inhalt aller Seiten wird mit dem HTML-Code der Layoutdatei gerendert.

## <a name="run-the-application"></a>Ausführen der Anwendung

Führen Sie jetzt die Anwendung aus, und zeigen Sie sie im Browser an. Sie können die Anwendung mit **STRG**+**F5** oder durch Klicken von **Debuggen** > **Ohne Debuggen starten** im Menü von Visual Studio ausführen.

## <a name="customize-the-application"></a>Anpassen der Anwendung

Fügen Sie eine Eigenschaft zur Datei *Index.cshtml.cs* hinzu, und legen Sie ihren Wert im `OnGet`-Handler auf die aktuelle Uhrzeit fest:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Ersetzen Sie den `<div>`-Inhalt in der Datei *Index.cshtml* durch folgendes Markup:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Führen Sie die Anwendung erneut aus. Die Seite sollte nun die aktuelle Uhrzeit anzeigen, jedoch ist es immer Mitternacht. Das ist nicht korrekt.

![Screenshot der Startseite der Anwendung in einem Browserfenster. Der Inhalt der Seite lautet: „Es ist jetzt 12:00 Uhr auf dem Server!“.](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Debuggen der Anwendung

Fügen Sie einen Breakpoint zur `OnGet`-Methode hinzu, in der Sie einen Wert zu `Time` zuweisen, und debuggen Sie nun die Anwendung.

Die Ausführung stoppt beim Breakpoint, und Sie können sehen, dass `DateTime.Today` das Datum enthält, aber die Uhrzeit immer Mitternacht ist, weil keine Uhrzeitdaten enthalten sind.

![Screenshot, der den Code für „Index.cshtml“ in Visual Studio zeigt. In der Zeile „Time = DateTime.Today.ToShortTimeString();“ ist ein Haltepunkt festgelegt.](media/vs-2019/vs2019-breakpoint.png)

Ändern Sie den Code so, dass `DateTime.Now` verwendet wird, und fahren Sie die Ausführung fort. Der neue Code für `OnGet` sollte wie folgt lauten:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Ihnen sollte nun die tatsächliche Serverzeit im Browser angezeigt werden, wenn Sie zur App navigieren.

> [!NOTE]
> Ihre Ausgabe kann von der Abbildung abweichen, da sich das Ausgabeformat von ToShortDateTimeString nach der aktuellen Einstellung der Kultur richtet. Siehe <xref:System.DateTime.ToShortTimeString>.

![Screenshot der Startseite der Anwendung in einem Browserfenster. Der Inhalt der Seite lautet: „Es ist jetzt 1:46 Uhr auf dem Server!“.](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Video erfahren Sie, wie Sie Ihrer App Unterstützung für Daten hinzufügen.

[Tutorial: Arbeiten mit Daten in Ihrer ASP.NET Core-App](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Weitere Informationen

- [Tutorial: Erstellen einer Razor Pages-Web-App mit ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)
