---
title: 'Tutorial: Erste Schritte mit C# und ASP.NET Core'
titleSuffix: ''
description: Dieser Artikel enthält eine ausführliche Anleitung zum Erstellen einer ASP.NET Core-Web-App mit C# in Visual Studio.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 15fcc5981c5711c7c3ddcf7262649a9d3473ee55
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833324"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutorial: Erste Schritte mit C# und ASP.NET Core in Visual Studio

In diesem Tutorial für die C#-Entwicklung mit ASP.NET Core in Visual Studio werden wir eine C#-ASP.NET Core-Web-App erstellen, Änderungen daran vornehmen, einige Funktionen der IDE kennenlernen und die App dann ausführen.

## <a name="before-you-begin"></a>Vorbereitungen

### <a name="install-visual-studio"></a>Installieren von Visual Studio

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

### <a name="update-visual-studio"></a>Aktualisieren von Visual Studio 2017

Wenn Sie Visual Studio bereits installiert haben, stellen Sie sicher, dass Sie das aktuelle Release ausführen. Weitere Informationen zum Aktualisieren Ihrer Installation finden Sie auf der Seite [Aktualisieren von Visual Studio auf die aktuelle Version](../../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Auswählen eines Designs (optional)

Die Screenshots in diesem Tutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](../../ide/quickstart-personalize-the-ide.md) entsprechende Anweisungen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst erstellen Sie ein ASP.NET Core-Projekt. Schon bevor Sie mit der Bearbeitung beginnen, enthält der Projekttyp alle Vorlagendateien, die Sie für eine voll funktionsfähige Website benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#** und anschließend **Web**, und klicken Sie auf **.NET Core**. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Web-App**. Nennen Sie die Datei *MyCoreApp*, und klicken Sie auf **OK**.

   ![Projektvorlage „ASP.NET Core-Webanwendung“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Hinzufügen einer Workload (optional)

Wenn Ihnen die Projektvorlage **ASP.NET Core-Webanwendung** fehlt, fügen Sie einfach die Workload **ASP.NET und Webentwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Verwenden des Dialogfelds „Neues Projekt“

1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**. (Abhängig von Ihren Anzeigeeinstellungen müssen Sie zur Anzeige möglicherweise scrollen.)

   ![Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../media/open-visual-studio-installer-mycoreapp.png)

1. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../media/tutorial-aspnet-workload.png)

   (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Verwenden der Menüleiste „Extras“

1. Schließen Sie das Dialogfeld **Neues Projekt**. Wählen Sie dann in der oberen Menüleiste **Extras** > **Get Tools and Features** (Tools und Features abrufen) aus.

1. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

### <a name="add-a-project-template"></a>Hinzufügen einer Projektvorlage

1. Klicken Sie im Dialogfeld **Neue ASP.NET Core-Webanwendung** auf die Projektvorlage **Webanwendung**.

1. Überprüfen Sie, ob **ASP.NET Core 2.1** im oberen Dropdownmenü angezeigt wird. Klicken Sie dann auf **OK**.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Wenn **ASP.NET Core 2.1** im oberen Dropdownmenü nicht angezeigt wird, stellen Sie sicher, dass Sie das neueste Release von Visual Studio ausführen. Weitere Informationen zum Aktualisieren Ihrer Installation finden Sie auf der Seite [Aktualisieren von Visual Studio auf die aktuelle Version](../../install/update-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *ASP.NET* ein. Wählen Sie anschließend in der Liste der Sprachen **C#** und dann aus der Liste der Plattformen **Windows** aus.

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **ASP.NET Core-Webanwendung** und dann **Weiter** aus.

   ![Wählen Sie die C#-Vorlage für die ASP.NET Core-Webanwendung aus](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Wenn die Vorlage **ASP.NET Core-Webanwendung** nicht angezeigt wird, können Sie sie über das Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **ASP.NET- und Webentwicklung** aus.
   >
   > ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Speichern Sie Ihre Arbeit, wenn Sie dazu aufgefordert werden. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise "[Projekt erstellen](#create-a-project)" zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname***MyCoreApp* ein. Wählen Sie anschließend **Erstellen** aus.

   ![Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „MyCoreApp“](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. Überprüfen Sie im Fenster **Neue ASP.NET Core-Webanwendung erstellen**, ob **ASP.NET Core 3.0** im oberen Dropdownmenü angezeigt wird. Wählen Sie dann **Webanwendung** aus; diese Option beinhaltet Razor Pages-Beispielseiten. Wählen Sie als Nächstes **Erstellen** aus.

   ![Fenster „Neue ASP.NET Core-Webanwendung erstellen“](./media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio öffnet Ihr neues Projekt.

::: moniker-end

### <a name="about-your-solution"></a>Die Projektmappe

Diese Lösung verwendet das **Razor Pages**-Entwurfsmuster. Dieses unterscheidet sich vom Entwurfsmuster [Model View Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) dadurch, dass es optimiert ist und den Modell- und Controllercode in die Razor Pages-Seite selbst einfügt.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Kennenlernen der Projektmappe

 1. Die Projektvorlage erstellt eine Projektmappe mit einem einzelnen ASP.NET Core-Projekt namens _MyCoreApp_. Wählen Sie die Registerkarte **Projektmappen-Explorer** aus, um den Inhalt anzuzeigen.

    ![ASP.NET-Projektmappen-Explorer in Visual Studio für die Razor Pages-Lösung namens MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Erweitern Sie den Ordner **Seiten** und dann *About.cshtml*.

     ![Datei „About.cshtml“ im Projektmappen-Explorer in Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Zeigen Sie die Datei **About.cshtml** im Code-Editor an.

     ![Screenshot: Erste zehn Zeilen der Datei „About.cshtml“ im Code-Editor von Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Wählen Sie die Datei **About.cshtml.cs** aus.

     ![Auswählen der Datei „About.cshtml.cs“ im Visual Studio-Code-Editor](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Zeigen Sie die Datei **About.cshtml.cs** im Code-Editor an.

     ![Screenshot: Erste 18 Zeilen der Datei „About.cshtml.cs“ im Code-Editor von Visual Studio ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Das Projekt enthält den Ordner **wwwroot**, der das Stammverzeichnis Ihrer Website ist. Erweitern Sie den Ordner, um den Inhalt anzuzeigen.

     ![Ordner „wwwroot“ im Projektmappen-Explorer in Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in die gewünschten Pfade einfügen.

 1. Das Projekt enthält auch Konfigurationsdateien, die die Web-App zur Laufzeit verwalten. Die [Standardkonfiguration](/aspnet/core/fundamentals/configuration) der Anwendung befindet sich in der Datei *appsettings.json*. Sie können diese Einstellungen jedoch auch mit *appsettings.Development.json* überschreiben. Erweitern Sie die Datei **appsettings.json**, um die Datei **appsettings.Development.json** anzuzeigen.

     ![Konfigurationsdateien im Projektmappen-Explorer in Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Ausführen, Debuggen und Vornehmen von Änderungen

1. Klicken Sie in der IDE auf die Schaltfläche **IIS Express**, um die App im Debugmodus zu erstellen und auszuführen. (Alternativ können Sie **F5** drücken oder in der Menüleiste **Debuggen** > **Debuggen starten** auswählen.)

     ![Die Schaltfläche „IIS Express“ in Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver "IIS Express" hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.
     >
     > Möglicherweise wird auch eine Meldung angezeigt, die Sie fragt, ob Sie ein IIS-SSL-Expresszertifikat akzeptieren möchten. Wählen Sie **Ja** aus, um den Code in einem Webbrowser anzuzeigen, und dann erneut **Ja**, wenn im Anschluss eine Sicherheitswarnung angezeigt wird.

1. Visual Studio startet ein Browserfenster. In der Menüleiste sollten die Seiten **Startseite**, **Info** und **Kontakt** angezeigt werden. (Wenn dies nicht der Fall ist, wählen Sie das Menüelement „Hamburger“ aus, um sie anzuzeigen.)

    ![Auswählen des Menüelements „Hamburger“ in der Menüleiste der Web-App](media/csharp-aspnet-razor-browser-page.png)

1. Wählen Sie in der Menüleiste **Info** aus.

   ![Auswählen von „Info“ in der Menüleiste im Browserfenster der App](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Auf der Seite **Info** im Browser wird u.a. der Text gerendert, der in der Datei *About.cshtml* festgelegt ist.

   ![Text auf der Seite „About“](media/csharp-aspnet-razor-browser-page-about.png)

1. Wechseln Sie zurück zu Visual Studio, und drücken Sie **UMSCHALT+F5**, um den Debugmodus zu beenden. Dadurch wird auch das Projekt im Browserfenster geschlossen.

1. Wählen Sie in Visual Studio **About.cshtml** aus. Löschen Sie das Wort _additional_, und fügen Sie an derselben Stelle _file and directory_ ein.

    ![Ändern des Texts in der Datei „About.cshtml“](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Wählen Sie **About.cshtml.cs** aus. Bereinigen Sie dann die `using`-Anweisungen oben in der Datei mithilfe der folgenden Verknüpfung.

   Wählen Sie eine der ausgegrauten `using`-Anweisungen aus, damit die Glühbirne für [Schnelle Aktionen](../../ide/quick-actions.md) unter dem Caretzeichen oder am linken Rand angezeigt wird. Klicken Sie zunächst auf die Glühbirne und anschließend auf **Nicht benötigte Using-Direktiven entfernen**.

   ![Entfernen unnötiger Using-Anweisungen in der Datei „About.cshtml.cs“](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio löscht die unnötigen `using`-Anweisungen aus der Datei.

1. Ändern Sie dann in der `OnGet()`-Methode den Text in den folgenden Code:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. **Environment** und **String** werden wellenförmig unterstrichen. Die Wellenlinien zeigen an, dass sich diese Typen nicht im gültigen Bereich befinden.

   ![Mit wellenförmigen Unterstrichen markierte Fehler in der OnGet-Methode](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Öffnen Sie die Symbolleiste **Fehlerliste**. Dort werden dieselben Fehler aufgelistet. (Wenn Ihnen die Symbolleiste **Fehlerliste** nicht angezeigt wird, klicken Sie in der oberen Menüleiste auf **Ansicht** > **Fehlerliste**.)

   ![Fehlerliste in Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Korrigieren wir dies. Platzieren Sie den Cursor im Code-Editor auf einer Zeile, die den Fehler enthält, und wählen Sie anschließend am linken Rand die Glühbirne für schnelle Aktionen aus. Wählen Sie im Dropdownmenü **using System;** aus, um diese Anweisung am Anfang der Datei hinzuzufügen und die Fehler zu beheben.

   ![Hinzufügen der „using System;“-Anweisung](media/csharp-aspnet-razor-add-usings.png)

1. Drücken Sie **STRG**+**S**, um Ihre Änderungen zu speichern, und drücken Sie dann **F5**, um Ihr Projekt im Webbrowser zu öffnen.

1. Klicken Sie oben auf der Website auf **Info**, um die Änderungen anzuzeigen.

   ![Anzeigen der aktualisierten „Info“-Seite mit den gemachten Änderungen](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Schließen Sie den Webbrowser, drücken Sie **UMSCHALT**+**F5**, um den Debugmodus zu beenden, und schließen Sie dann Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Kennenlernen der Projektmappe

 1. Die Projektvorlage erstellt eine Projektmappe mit einem einzelnen ASP.NET Core-Projekt namens _MyCoreApp_. Wählen Sie die Registerkarte **Projektmappen-Explorer** aus, um den Inhalt anzuzeigen.

    ![ASP.NET-Projektmappen-Explorer in Visual Studio für die Razor Pages-Lösung namens MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Erweitern Sie den Ordner **Seiten**.

     ![Ordner „Seiten“ im Projektmappen-Explorer](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Zeigen Sie die Datei **Index.cshtml** im Code-Editor an.

     ![Anzeigen der Datei „Index.cshtml“ im Code-Editor von Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Jede CSHTML-Datei verfügt über eine zugeordnete Codedatei. Erweitern Sie zum Öffnen der Codedatei im Editor den Knoten **Index.cshtml** im Projektmappen-Explorer, und klicken Sie auf die Datei **Index.cshtml.cs**.

     ![Auswählen der Datei „Index.cshtml.cs“ im Code-Editor von Visual Studio](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Zeigen Sie die Datei **Index.cshtml.cs** im Code-Editor an.

     ![Anzeigen der Datei „About.cshtml“ im Visual Studio-Code-Editor](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Das Projekt enthält den Ordner **wwwroot**, der das Stammverzeichnis Ihrer Website ist. Erweitern Sie den Ordner, um den Inhalt anzuzeigen.

     ![Ordner „wwwroot“ im Projektmappen-Explorer in Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in die gewünschten Pfade einfügen.

 1. Das Projekt enthält auch Konfigurationsdateien, die die Web-App zur Laufzeit verwalten. Die [Standardkonfiguration](/aspnet/core/fundamentals/configuration) der Anwendung befindet sich in der Datei *appsettings.json*. Sie können diese Einstellungen jedoch auch mit *appsettings.Development.json* überschreiben. Erweitern Sie die Datei **appsettings.json**, um die Datei **appsettings.Development.json** anzuzeigen.

     ![Konfigurationsdateien im Projektmappen-Explorer in Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Ausführen, Debuggen und Vornehmen von Änderungen

1. Klicken Sie in der IDE auf die Schaltfläche **IIS Express**, um die App im Debugmodus zu erstellen und auszuführen. (Alternativ können Sie **F5** drücken oder in der Menüleiste **Debuggen** > **Debuggen starten** auswählen.)

     ![Die Schaltfläche „IIS Express“ in Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver "IIS Express" hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.
     >
     > Möglicherweise wird auch eine Meldung angezeigt, die Sie fragt, ob Sie ein IIS-SSL-Expresszertifikat akzeptieren möchten. Wählen Sie **Ja** aus, um den Code in einem Webbrowser anzuzeigen, und dann erneut **Ja**, wenn im Anschluss eine Sicherheitswarnung angezeigt wird.

1. Visual Studio startet ein Browserfenster. In der Menüleiste sollten die Seiten **Startseite** und **Datenschutz** angezeigt werden.

1. Wählen Sie in der Menüleiste die Option **Datenschutz** aus.

   Im Browser wird auf der Seite **Datenschutz** der in der Datei *Privacy.cshtml* festgelegte Text gerendert.

   ![Anzeigen des Texts auf der Seite „Datenschutz“](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Wechseln Sie zurück zu Visual Studio, und drücken Sie **UMSCHALT+F5**, um den Debugmodus zu beenden. Dadurch wird auch das Projekt im Browserfenster geschlossen.

1. Öffnen Sie in Visual Studio die Datei **Privacy.cshtml**, um sie zu bearbeiten. Löschen Sie den Satz _Verwenden Sie diese Seite, um Details über die Datenschutzrichtlinie Ihrer Website anzugeben_, und fügen Sie stattdessen die Worte _Diese Seite wird aktuell überarbeitet (Stand @ViewData["TimeStamp"])_ hinzu.

    ![Ändern des Texts in der Datei „Privacy.cshtml“](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Nehmen Sie nun eine Codeänderung vor. Wählen Sie die Datei **Privacy.cshtml.cs** aus. Bereinigen Sie dann die `using`-Anweisungen oben in der Datei mithilfe der folgenden Verknüpfung.

   Wählen Sie eine der ausgegrauten `using`-Anweisungen aus, damit die Glühbirne für [Schnelle Aktionen](../../ide/quick-actions.md) unter dem Caretzeichen oder am linken Rand angezeigt wird. Klicken Sie zunächst auf die Glühbirne, und zeigen Sie anschließend auf **Nicht benötigte Using-Direktiven entfernen**.

   ![Entfernen nicht benötigter Using-Direktiven in der Datei „Privacy.cshtml.cs“](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Klicken Sie auf **Vorschau der Änderungen**, um die Änderungen anzuzeigen.

   ![Vorschau der Änderungen](media/vs-2019/csharp-aspnet-preview-changes.png)

   Wählen Sie **Anwenden** aus. Visual Studio löscht die unnötigen `using`-Anweisungen aus der Datei.

1. Ändern Sie dann in der `OnGet()`-Methode den Text in den folgenden Code:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Beachten Sie, dass **DateTime** wellenförmig unterstrichen wird. Die Wellenlinie zeigt an, dass sich dieser Typ nicht im gültigen Bereich befindet.

   ![Mit wellenförmigen Unterstrichen markierte Fehler in der OnGet-Methode](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Öffnen Sie die Symbolleiste **Fehlerliste**. Dort werden dieselben Fehler aufgelistet. (Wenn Ihnen die Symbolleiste **Fehlerliste** nicht angezeigt wird, klicken Sie in der oberen Menüleiste auf **Ansicht** > **Fehlerliste**.)

   ![Fehlerliste in Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Korrigieren wir dies. Platzieren Sie den Cursor im Code-Editor auf einer Zeile, die den Fehler enthält, und wählen Sie anschließend am linken Rand die Glühbirne für schnelle Aktionen aus. Wählen Sie im Dropdownmenü **using System;** aus, um diese Anweisung am Anfang der Datei hinzuzufügen und die Fehler zu beheben.

   ![Hinzufügen der „using System;“-Anweisung](media/vs-2019/csharp-aspnet-add-usings.png)

1. Drücken Sie **F5**, um das Projekt im Webbrowser zu öffnen.

1. Klicken Sie oben auf der Website auf **Datenschutz**, um die Änderungen anzuzeigen.

   ![Anzeigen der aktualisierten Seite „Datenschutz“ mit den vorgenommenen Änderungen](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Schließen Sie den Webbrowser, drücken Sie **UMSCHALT**+**F5**, um den Debugmodus zu beenden, und schließen Sie dann Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Schnelle Antworten zu häufig gestellten Fragen

Im folgenden kurzen Abschnitt zu häufig gestellten Fragen werden einige wichtige Konzepte besprochen.

### <a name="what-is-c"></a>Was ist C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) ist eine typsichere und objektorientierte Programmiersprache, die nicht nur stabil, sondern auch einfach zu erlernen ist.

### <a name="what-is-aspnet-core"></a>Was ist ASP.NET Core?

ASP.NET Core ist ein plattformübergreifendes Open Source-Framework zum Erstellen von Anwendungen mit Internetverbindung, wie etwa Web-Apps und -dienste. ASP.NET Core-Apps können unter .NET Core oder .NET Framework ausgeführt werden. Sie können Ihre ASP.NET Core-Apps plattformübergreifend unter Windows, macOS und Linux ausführen und entwickeln. ASP.NET Core ist auf [GitHub](https://github.com/aspnet/home) verfügbar.

### <a name="what-is-visual-studio"></a>Was ist Visual Studio?

Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE gelernt haben. Weitere Informationen zum Erstellen einer Web-App oder Website mit C# und ASP.NET Core finden Sie in den folgenden Tutorials:

> [!div class="nextstepaction"]
> [Erstellen einer Razor-Seiten-Web-App mit ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Siehe auch

[Veröffentlichen Ihrer Web-App in Azure App Service mit Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
