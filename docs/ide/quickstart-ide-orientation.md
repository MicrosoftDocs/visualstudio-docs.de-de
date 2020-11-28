---
title: 'Schnellstart: Einführung in die Visual Studio-IDE'
description: Hier erfahren Sie mehr über einige Fenster, Menüs und andere Benutzeroberflächenfeatures der integrierten Entwicklungsumgebung (IDE) von Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4511658a454c1431967905e88428842c3ba00c64
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870885"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Schnellstart: Ein erster Blick auf die Visual Studio-IDE

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio unternehmen wir eine Tour durch einige der Fenster, Menüs und andere Funktionen der Benutzeroberfläche.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Startseite

Das Erste, was Sie nach dem Öffnen von Visual Studio sehen, ist wahrscheinlich die **Startseite**. Die **Startseite** ist als „Hub“ konzipiert, um Ihnen zu helfen, die benötigten Befehle und Projektdateien schneller zu finden. Der Abschnitt **Aktuell** zeigt Projekte und Ordner an, an denen Sie zuletzt gearbeitet haben. Unter **Neues Projekt** können Sie auf einen Link klicken, um das Dialogfeld **Neues Projekt** aufzurufen, oder Sie können unter **Öffnen** ein vorhandenes Codeprojekt oder einen Codeordner öffnen. Auf der rechten Seite befindet sich ein Feed mit den neuesten Entwicklernews.

![Startseite in Visual Studio](media/start-page.png)

Wenn Sie die **Startseite** schließen und dann erneut anzeigen möchten, können Sie sie im Menü **Datei** erneut öffnen.

![Dateimenü in Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Startfenster

Das Erste, was Sie nach dem Öffnen von Visual Studio sehen, ist das Startfenster. Das Startfenster ist so entworfen, dass Sie möglichst schnell auf den Code zugreifen können. Im Startfenster finden Sie Optionen zum Klonen oder Ausschecken von Code, zum Öffnen bereits vorhandener Projekte oder Projektmappe, zum Erstellen eines neuen Projekts oder einfach zum Öffnen eines Ordners mit Codedateien.

[![Startfenster in Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Wenn Sie Visual Studio zum ersten Mal benutzen, bleibt die Liste zuletzt geöffneter Projekte leer.

Wenn Sie mit einer nicht auf MSBuild basierenden Codebasis arbeiten, verwenden Sie die Option **Lokalen Ordner öffnen**, um Ihren Code in Visual Studio zu öffnen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](develop-code-in-visual-studio-without-projects-or-solutions.md). Andernfalls können Sie ein neues Projekt erstellen oder ein Projekt von einem Quellenanbieter wie GitHub oder Azure DevOps klonen.

Die Option **Ohne Code fortfahren** öffnet einfach nur die Entwicklungsumgebung von Visual Studio, ohne dass spezielle Projekte oder Code geladen würden. Sie können diese Option auch dazu verwenden, um einer [Live Share](/visualstudio/liveshare/)-Sitzung beizutreten, oder Anfügungen an einen Prozess zum Debuggen durchzuführen. Sie können auch **Esc** drücken, um das Startfenster zu schließen, und die IDE zu öffnen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie ein neues Projekt, um die Features in Visual Studio besser kennenzulernen.

::: moniker range="vs-2017"

1. Geben Sie auf der **Startseite** im Suchfeld unter **Neues Projekt** **Konsole** ein, um die Liste der Projekttypen nach denen zu filtern, die „Konsole“ im Namen enthalten.

   ![Suchen von Projektvorlagen auf der Visual Studio-Startseite](media/start-page-search-templates.png)

   Visual Studio stellt mehrere Arten von Projektvorlagen bereit, durch die Sie schnell mit dem Programmieren beginnen können. Wählen Sie eine C#-Projektvorlage für eine **Konsolen-App (.NET Core)** aus. (Wenn Sie mit Visual Basic, C++, JavaScript oder einer anderen Sprache entwickeln, können Sie alternativ ein Projekt in einer dieser Sprachen erstellen. Die Benutzeroberfläche, die angezeigt wird, ist für alle Programmiersprachen ähnlich.)

1. Übernehmen Sie im angezeigten Dialogfeld **Neues Projekt** den Standardprojektnamen, und klicken Sie anschließend auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Ein Dialogfeld mit dem Titel **Neues Projekt erstellen** wird geöffnet. Hier können Sie nach Projektvorlagen suchen, sie filtern und sie auswählen. Außerdem wird hier eine Liste mit Ihren zuletzt verwendeten Projektvorlagen angezeigt.

1. Geben Sie im Suchfeld am oberen Rand **Konsole** ein, um die Liste mit den Projekttypen nach Einträgen zu filtern, die das Wort „Konsole“ enthalten. Grenzen Sie die Suchergebnisse weiter ein, indem Sie unter **Sprache** die Option **C#** (oder eine andere Programmiersprache) auswählen.

   ![Dialogfeld „Neues Projekt“ in Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Wenn Sie C#, Visual Basic oder F# als Programmiersprache ausgewählt haben, wählen Sie die Vorlage **Konsolen-App (.NET Core)** aus, und klicken Sie auf **Weiter**. (Falls Sie eine andere Programmiersprache ausgewählt haben, wählen Sie einfach eine beliebige Vorlage aus. Die Benutzeroberfläche, die angezeigt wird, ist für alle Programmiersprachen ähnlich.)

1. Übernehmen Sie auf der Seite **Neues Projekt konfigurieren** die Standardwerte für Projektname und Speicherort, und wählen Sie anschließend **Erstellen** aus.

::: moniker-end

   Das Projekt wird erstellt, und eine Datei namens *Program.cs* wird im Fenster **Editor** geöffnet. Der **Editor** zeigt den Inhalt von Dateien an. Dort erledigen Sie den Großteil der Programmierarbeit in Visual Studio.

   ![Editor in Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Projektmappen-Explorer

Im **Projektmappen-Explorer**, der sich in Visual Studio üblicherweise auf der rechten Seite befindet, wird eine grafische Darstellung der Hierarchie von Dateien und Ordnern in Ihrem Projekt-, Projektmappen- oder Codeordner angezeigt. Sie können die Hierarchie durchsuchen und im **Projektmappen-Explorer** zu einer Datei navigieren.

![Projektmappen-Explorer in Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüs

Die Menüleiste am oberen Rand der Visual Studio-Gruppen gruppiert Befehle in Kategorien. Beispielsweise enthält das Menü **Projekt** Befehle, die sich auf das Projekt beziehen, in dem Sie zurzeit arbeiten. Im Menü **Extras** können Sie das Verhalten von Visual Studio anpassen, indem Sie auf **Optionen** klicken, oder Features zu Ihrer Installation hinzufügen, indem Sie auf **Tools und Features abrufen** klicken.

::: moniker range="vs-2017"

![Menüleiste in Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menüleiste in Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Fehlerliste

Öffnen Sie das Fenster **Fehlerliste**, indem Sie zuerst das Menü **Ansicht** und anschließend **Fehlerliste** auswählen.

Die **Fehlerliste** zeigt Fehler, Warnungen und Meldungen zum aktuellen Zustand Ihres Codes an. Wenn in Ihrer Datei oder Ihrem Projekt Fehler vorhanden sind (z.B. eine fehlende Klammer oder ein fehlendes Semikolon), werden diese hier aufgelistet.

![Fehlerliste in Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Ausgabefenster

Im **Ausgabefenster** werden Ausgabemeldungen von der Erstellung Ihres Projekts sowie vom Anbieter der Quellcodeverwaltung angezeigt.

Erstellen Sie das Projekt, um die Buildausgaben anzuzeigen. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus. Das Fenster **Ausgabe** erhält den Fokus automatisch und zeigt eine Meldung zu einem erfolgreichen Buildvorgang an.

![Ausgabefenster in Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Suchfeld

Über das Suchfeld gelangen Sie schnell und einfach an nahezu jeden Ort in Visual Studio. Sie können Text eingeben, der sich auf die gewünschte Aufgabe bezieht. Dann wird eine Liste von Optionen angezeigt, die sich für den Text eignen. Angenommen, Sie möchten z.B. die Ausführlichkeit der Buildausgabe erhöhen, um Details dazu anzuzeigen, was genau im Build geschieht. Sie könnten folgendermaßen vorgehen:

::: moniker range="vs-2017"

1. Das Suchfeld **Schnellstart** finden Sie in der rechten oberen Ecke der IDE. (Alternativ können Sie die Tastenkombination **STRG**+**Q** verwenden.)

2. Geben Sie im Suchfeld den Suchbegriff **Ausführlichkeit** ein. Klicken Sie in den angezeigten Ergebnissen unter der Kategorie **Optionen** auf **Projekte und Projektmappen > Erstellen und ausführen**.

   ![Suchfeld „Schnellstart“ in Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   Das Dialogfeld **Optionen** wird mit der Seite **Erstellen und ausführen** geöffnet.

::: moniker-end

::: moniker range=">=vs-2019"

1. Drücken Sie **STRG**+**Q**, um das Suchfeld im oberen Bereich der integrierten Entwicklungsumgebung zu aktivieren.

2. Geben Sie im Suchfeld den Suchbegriff **Ausführlichkeit** ein. Wählen Sie in den angezeigten Ergebnissen die Option **MSBuild-Ausführlichkeit ändern**.

   ![Screenshot: Suchfeld in Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   Das Dialogfeld **Optionen** wird mit der Seite **Erstellen und ausführen** geöffnet.

::: moniker-end

3. Wählen Sie unter **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** aus, und klicken Sie dann auf die Schaltfläche **OK**.

4. Erstellen Sie das Projekt erneut, indem Sie mit der rechten Maustaste auf das Projekt **ConsoleApp1** im **Projektmappen-Explorer** klicken und **Neu erstellen** aus dem Kontextmenü auswählen.

   Nun zeigt das Fenster **Ausgabe** eine ausführlichere Protokollierung des Erstellungsprozesses an, z.B. auch, wohin welche Dateien kopiert wurden.

   ![Ausführliche Buildausgabe in Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menü „Feedback senden“

Wenn Sie Probleme bei der Verwendung von Visual Studio oder Vorschläge zur Verbesserung des Produkts haben, können Sie das Menü **Feedback senden** im oberen Bereich des Visual Studio-Fensters verwenden.

::: moniker range="vs-2017"

![Menü „Feedback senden“ in Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menü „Feedback senden“ in Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Wir haben uns nur einige der Features von Visual Studio angesehen, um uns mit der Benutzeroberfläche vertraut zu machen. Weitere mögliche Schritte:

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über den Code-Editor](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Weitere Informationen

- [Übersicht der Visual Studio-IDE](../get-started/visual-studio-ide.md)
- [Features von Visual Studio](../ide/advanced-feature-overview.md)
- [Ändern von Design und Schriftfarben](../ide/quickstart-personalize-the-ide.md)
