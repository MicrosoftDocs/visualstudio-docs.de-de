---
title: Erste Schritte mit C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645628"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Erste Schritte mit C++ in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, werden Sie mit vielen Tools und Dialogfeldern vertraut, die Sie für die Entwicklung von Anwendungen in Visual Studio verwenden können. Sie erstellen eine einfache "Hello, World"-Anwendung und lernen dabei die Arbeiten in der integrierten Entwicklungsumgebung (IDE) kennen.

 Dieses Thema enthält folgende Abschnitte:

 [Melden Sie sich bei Visual Studio an.](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Erstellen einer einfachen Anwendung](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Hinzufügen von Code zur Anwendung](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Debuggen und Testen der Anwendung](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Erstellen einer Releaseversion der APP](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Melden Sie sich bei Visual Studio an.
 Wenn Sie Visual Studio zum ersten Mal starten, erhalten Sie die Möglichkeit, sich mit einem Microsoft-Konto, z. B. Live oder Outlook, anzumelden. Durch die Anmeldung können Sie Ihre Einstellungen mit allen Geräten synchronisieren. Weitere Informationen finden Sie unter [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md)

 Abbildung 1: Visual Studio-IDE

 ![IDE mit angewendeten Visual C&#43;&#43;-Einstellungen](../ide/media/c-ide-defaultenvironmentlayout.png "C++ IDE_DefaultEnvironmentLayout")

 Wenn Sie Visual Studio geöffnet haben, können Sie die drei grundlegenden Teile der IDE sehen: Toolsfenster, Menüs und Symbolleisten und den Hauptfensterbereich. Mit **Schnellstart**werden Toolfenster auf der linken und rechten Seite des Anwendungsfensters und die Menüleiste und die Standardsymbolleiste oben angedockt. In der Mitte des Anwendungsfensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt öffnen, werden Editoren und Designer in diesem Bereich angezeigt. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Erstellen einer einfachen Anwendung
 Wenn Sie eine App in Visual Studio erstellen, erstellen Sie zunächst ein Projekt und eine Projektmappe. Für dieses Beispiel erstellen Sie eine Windows-Konsolenanwendung.

#### <a name="to-create-a-console-app"></a>Erstellen einer Konsolen-App

1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.

    ![Wählen Sie in der Menüleiste „Datei > Neu > Projekt“ aus.](../ide/media/exploreide-filenewproject.png "Exploreide-filenewproject")

2. Wählen Sie in der **Visual C++** Kategorie die Vorlage **Win32-Konsolenanwendung** aus, und nennen Sie das Projekt `GreetingsConsoleApp`.

    ![Vorlage für eine Win32-Konsolenanwendung](../ide/media/c-ide-newprojectdlg.png "C++ IDE_NewProjectDlg")

3. Wenn der Win32-Anwendungs-Assistent angezeigt wird, wählen Sie die Schaltfläche **Fertig stellen** aus.

    ![Assistent für Win32-Konsolenanwendung](../ide/media/c-ide-win32consoleappwizard.png "C++ IDE_Win32ConsoleAppWizard")

   Das Projekt und die Projektmappe "GreetingsConsoleApp", mit den grundlegenden Dateien für eine Win32-Konsolen-App, werden erstellt und in **Projektmappen-Explorer**automatisch geladen. Die Datei "GreetingsConsoleApp.cpp" wird im Code-Editor geöffnet. Die folgenden Elemente werden in **Projektmappen-Explorer**angezeigt:

   Abbildung 4: Projektelemente

   ![Dateien für die Projektmappe im Projektmappen-Explorer](../ide/media/c-ide-solutioncontents.png "C++ IDE_SolutionContents")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> Hinzufügen von Code zur Anwendung
 Als Nächstes fügen Sie Code hinzu, um das Wort "Hello" im Konsolenfenster anzuzeigen.

#### <a name="to-display-hello-in-the-console-window"></a>Anzeigen von "Hello" im Konsolenfenster

1. Geben Sie in der Datei "GreetingsConsoleApp.cpp" vor der Zeile `return 0;` eine Leerzeile und dann den folgenden Code ein:

    ```
    cout << "Hello\n";
    ```

     Eine rote Wellenlinie wird unter `cout`angezeigt. Wenn Sie darauf zeigen, wird eine Fehlermeldung angezeigt.

     ![Fehlertext für "cout"](../ide/media/c-ide-couterror.png "C++ IDE_CoutError")

     Die Fehlermeldung wird auch im Fenster **Fehlerliste** angezeigt. Sie können das Fenster auch anzeigen, indem Sie in der Menüleiste **Ansicht**die Option **Fehlerliste**auswählen.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) ist in der \<iostream\> Header Datei enthalten.

2. Um den iostream-Header einzuschließen, geben Sie den folgenden Code nach `#include "stdafx.h"`ein:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Wahrscheinlich haben Sie bemerkt, dass während der Codeeingabe ein Feld mit Empfehlungen für die Zeichen angezeigt wird, die Sie eingegeben haben. Dieses Feld ist Teil von C++-IntelliSense, das Code-Eingabeaufforderungen bietet, darunter Auflistungen der Klassen- oder Schnittstellen-Member sowie der Parameterinformationen. Außerdem können Sie Codeausschnitte verwenden, wobei es sich um vordefinierte Codeblöcke handelt. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md) und [Code Ausschnitten](../ide/code-snippets.md).

     Die rote Wellenlinie unter `cout` wird ausgeblendet, wenn Sie den Fehler korrigieren.

3. Speichern Sie die Änderungen in der Datei.

     ![Code zum Beheben des cout-Fehlers](../ide/media/c-ide-coutfix.png "C++ IDE_CoutFix")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Debuggen und Testen der Anwendung
 Sie können "GreetingsConsoleApp" debuggen, um festzustellen, ob das Wort "Hello" im Konsolenfenster angezeigt wird.

#### <a name="to-debug-the-application"></a>So debuggen Sie die Anwendung

- Starten Sie den Debugger.

     ![Befehl "Debugging starten" im Menü "Debuggen"](../ide/media/exploreide-startdebugging.png "Exploreide-Startdebugging")

     Die Debugger wird gestartet und führt den Code aus. Das Konsolenfenster (ein separates Fenster, das wie eine Eingabeaufforderung aussieht) wird ein paar Sekunden lang angezeigt, wird jedoch schnell geschlossen, wenn der Debugger anhält. Um den Text anzuzeigen, müssen Sie einen Haltepunkt festlegen, um die Ausführung des Programms zu beenden.

#### <a name="to-add-a-breakpoint"></a>Hinzufügen eines Haltepunktes

1. Fügen Sie über die Menüleiste in der Zeile `return 0;`einen Haltepunkt hinzu. Sie können auch einfach in den linken Rand klicken, um einen Haltepunkt zu setzen.

    ![Befehl "Haltepunkt umschalten" im Menü "Debuggen"](../ide/media/exploreide-togglebreakpoint.png "Exploreide-Objekt")

    Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

2. Drücken Sie die F5-TASTE, um das Debuggen zu starten.

    Der Debugger wird gestartet, und ein Konsolenfenster mit dem Wort **Hello**wird angezeigt.

    ![„Hello“-Text im Windows-Befehlseingabeaufforderungsfenster](../ide/media/c-ide-hellocommandwindow.png "C++ IDE_HelloCommandWindow")

3. Drücken Sie UMSCHALT + F5, um den Debugvorgang zu beenden.

   Weitere Informationen finden Sie unter [Konsolenprojekte](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a>Erstellen einer Releaseversion der App
 Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Bereinigen der Projektmappendateien und Erstellen einer Releaseversion

1. Löschen Sie in der Menüleiste Zwischendateien und Ausgabedateien, die bei vorherigen Builds erstellt wurden.

    ![Befehl "Projektmappe bereinigen" im Menü "Erstellen"](../ide/media/exploreide-cleansolution.png "Exploreide-cleansolution")

2. Ändern Sie die Buildkonfiguration für GreetingsConsoleApp von **Debuggen** zu **Version**.

    ![Version der Anwendung erstellen](../ide/media/c-ide-changingbuildtorelease.png "C++ IDE_ChangingBuildtoRelease")

3. Erstellen Sie die Projektmappe.

    ![Befehl "Projektmappe erstellen" im Menü "Erstellen"](../ide/media/exploreide-buildsolution.png "Exploreide-BUILDSOLUTION")

   Herzlichen Glückwunsch, Sie haben diese exemplarischen Vorgehensweise abgeschlossen! Weitere Beispiele zum Durcharbeiten finden Sie unter [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Weitere Informationen
 [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [Produktivitätstipps](../ide/productivity-tips-for-visual-studio.md) [Visual Studio-Beispiele](../ide/visual-studio-samples.md) [Erste Schritte beim Entwickeln mit Visual Studio](../ide/get-started-developing-with-visual-studio.md)
