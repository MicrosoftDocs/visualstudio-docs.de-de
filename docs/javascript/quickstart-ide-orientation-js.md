---
title: Einführung in die Visual Studio-IDE
description: Hier erfahren Sie mehr über die integrierte Entwicklungsumgebung (IDE) von Visual Studio einschließlich der Fenster, Menüs und anderen Benutzeroberflächenfeatures, die am häufigsten verwendet werden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f80dd85e1cc8f93784ed938ef1788730b3c926e8
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947816"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Einführung in die Visual Studio-IDE

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio unternehmen wir eine Tour durch einige der Fenster, Menüs und andere Funktionen der Benutzeroberfläche.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Startfenster

Das erste, was Sie nach dem Start von Visual Studio sehen, ist das Startfenster. Das Startfenster ist so entworfen, dass Sie möglichst schnell auf den Code zugreifen können. Im Startfenster finden Sie Optionen zum Schließen oder Überprüfen von Code, zum Öffnen von bestehenden Projekten oder Projektmappen, zum Erstellen eines neuen Projekts, oder einfach zum Öffnen eines Ordners, der Codedateien enthält.

[![Startfenster in Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Wenn Sie Visual Studio zum ersten Mal benutzen, bleibt die Liste zuletzt geöffneter Projekte leer.

Wenn Sie mit einer nicht auf MSBuild basierenden Codebasis arbeiten, verwenden Sie die Option **Lokalen Ordner öffnen** , um Ihren Code in Visual Studio zu öffnen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](develop-javascript-code-without-solutions-projects.md). Andernfalls können Sie ein neues Projekt erstellen oder ein Projekt von einem Quellenanbieter wie GitHub oder Azure DevOps klonen.

Die Option **Ohne Code fortfahren** öffnet einfach nur die Entwicklungsumgebung von Visual Studio, ohne dass spezielle Projekte oder Code geladen würden. Sie können diese Option auch dazu verwenden, um einer [Live Share](/visualstudio/liveshare/)-Sitzung beizutreten, oder Anfügungen an einen Prozess zum Debuggen durchzuführen. Sie können auch **Esc** drücken, um das Startfenster zu schließen, und die IDE zu öffnen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Startseite

Das erste, was Sie nach dem Start von Visual Studio sehen, ist wahrscheinlich die **Startseite** . Die **Startseite** ist als „Hub“ konzipiert, um Ihnen zu helfen, die benötigten Befehle und Projektdateien schneller zu finden. Der Abschnitt **Aktuell** zeigt Projekte und Ordner an, an denen Sie zuletzt gearbeitet haben. Unter **Neues Projekt** können Sie auf einen Link klicken, um das Dialogfeld **Neues Projekt** aufzurufen, oder Sie können unter **Öffnen** ein vorhandenes Codeprojekt oder einen Codeordner öffnen. Auf der rechten Seite befindet sich ein Feed mit den neuesten Entwicklernews.

![Startseite in Visual Studio](media/start-page.png)

Wenn Sie die **Startseite** schließen und dann erneut anzeigen möchten, können Sie sie im Menü **Datei** erneut öffnen.

![Dateimenü in Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie ein neues Projekt, um die Features in Visual Studio besser kennenzulernen.

::: moniker range=">=vs-2019"

1. Wählen Sie im Startfenster die Option **Neues Projekt erstellen** aus, und geben Sie dann im Suchfeld **javascript** ein, um die Liste der Projekttypen nach denen zu filtern, die „javascript“ im Namen oder Sprachtyp enthalten.

   Visual Studio stellt mehrere Arten von Projektvorlagen bereit, durch die Sie schnell mit dem Programmieren beginnen können. (Alternativ können Sie das Projekt auch in TypeScript erstellen, wenn Sie damit vertraut sind. Die Benutzeroberfläche, die angezeigt wird, ist für alle Programmiersprachen ähnlich.)

   ![Suchen von Projektvorlagen im Visual Studio-Startfenster](media/vs-2019/create-new-project.png)

1. Wählen Sie die Projektvorlage **Leere Node.js-Webanwendung** aus, und klicken Sie dann auf **Weiter** .

1. Übernehmen Sie im angezeigten Dialogfeld **Neues Projekt konfigurieren** den Standardprojektnamen, und klicken Sie anschließend auf **Erstellen** .

::: moniker-end

::: moniker range="vs-2017"

1. Geben Sie auf der **Startseite** im Suchfeld unter **Neues Projekt** **javascript** ein, um die Liste der Projekttypen nach denen zu filtern, die „javascript“ im Namen oder Sprachtyp enthalten.

   ![Suchen von Projektvorlagen auf der Visual Studio-Startseite](media/start-page-search-templates.png)

   Visual Studio stellt mehrere Arten von Projektvorlagen bereit, durch die Sie schnell mit dem Programmieren beginnen können. Wählen Sie die Projektvorlage **Leere Node.js-Webanwendung** aus. (Alternativ können Sie das Projekt auch in TypeScript erstellen, wenn Sie damit vertraut sind. Die Benutzeroberfläche, die angezeigt wird, ist für alle Programmiersprachen ähnlich.)

1. Übernehmen Sie im angezeigten Dialogfeld **Neues Projekt** den Standardprojektnamen, und klicken Sie anschließend auf **OK** .
::: moniker-end

   Das Projekt wird erstellt, und eine Datei namens *server.js* wird im Fenster **Editor** geöffnet. Der **Editor** zeigt den Inhalt von Dateien an und ist der Ort, an dem Sie den Großteil Ihrer Codierungsaufgaben in Visual Studio erledigen.

   ![Editor in Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Projektmappen-Explorer

Im **Projektmappen-Explorer** , der sich in Visual Studio üblicherweise auf der rechten Seite befindet, wird eine grafische Darstellung der Hierarchie von Dateien und Ordnern in Ihrem Projekt-, Projektmappen- oder Codeordner angezeigt. Sie können die Hierarchie durchsuchen und im **Projektmappen-Explorer** zu einer Datei navigieren.

![Projektmappen-Explorer in Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüs

Die Menüleiste am oberen Rand der Visual Studio-Gruppen gruppiert Befehle in Kategorien. Beispielsweise enthält das Menü **Projekt** Befehle, die sich auf das Projekt beziehen, in dem Sie zurzeit arbeiten. Im Menü **Extras** können Sie das Verhalten von Visual Studio anpassen, indem Sie auf **Optionen** klicken, oder Features zu Ihrer Installation hinzufügen, indem Sie auf **Tools und Features abrufen** klicken.

![Menüleiste in Visual Studio](media/quickstart-IDE-menu-bar.png)

Öffnen Sie das Fenster **Fehlerliste** , indem Sie erst auf das Menü **Ansicht** und dann auf **Fehlerliste** klicken.

## <a name="error-list"></a>Fehlerliste

Die **Fehlerliste** zeigt Fehler, Warnungen und Meldungen zum aktuellen Zustand Ihres Codes an. Wenn in Ihrer Datei oder Ihrem Projekt Fehler vorhanden sind (z.B. eine fehlende Klammer oder ein fehlendes Semikolon), werden diese hier aufgelistet.

![Fehlerliste in Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Ausgabefenster

Im **Ausgabefenster** werden Ausgabemeldungen von der Erstellung Ihres Projekts sowie vom Anbieter der Quellcodeverwaltung angezeigt.

Erstellen Sie das Projekt, um die Buildausgaben anzuzeigen. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus. Das Fenster **Ausgabe** erhält den Fokus automatisch und zeigt eine Meldung zu einem erfolgreichen Buildvorgang an.

![Ausgabefenster in Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Suchfeld

Das Suchfeld bietet eine schnelle und einfache Möglichkeit, fast alle Aufgaben in Visual Studio auszuführen. Sie können Text eingeben, der sich auf die gewünschte Aufgabe bezieht. Dann wird eine Liste von Optionen angezeigt, die sich für den Text eignen. Angenommen, Sie möchten z.B. die Ausführlichkeit der Buildausgabe erhöhen, um Details dazu anzuzeigen, was genau im Build geschieht. Sie könnten folgendermaßen vorgehen:

1. Geben Sie im Suchfeld den Suchbegriff **Ausführlichkeit** ein. Klicken Sie in den angezeigten Ergebnissen unter der Kategorie **Optionen** auf **Projekte und Projektmappen > Erstellen und ausführen** .

   ![Suchfeld in Visual Studio](media/quickstart-IDE-quick-launch.png)

   Das Dialogfeld **Optionen** wird mit der Seite **Erstellen und ausführen** geöffnet.

1. Wählen Sie unter **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** aus, und klicken Sie dann auf die Schaltfläche **OK** .

1. Erstellen Sie das Projekt erneut, indem Sie mit der rechten Maustaste auf das Projekt **NodejsWebApp1** im **Projektmappen-Explorer** klicken und **Neu erstellen** aus dem Kontextmenü auswählen.

   Nun zeigt das Fenster **Ausgabe** eine ausführlichere Protokollierung des Erstellungsprozesses an, z.B. auch, wohin welche Dateien kopiert wurden.

   ![Ausführliche Buildausgabe in Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menü „Feedback senden“

Wenn Sie Probleme bei der Verwendung von Visual Studio oder Vorschläge zur Verbesserung des Produkts haben, können Sie das Menü **Feedback senden** ganz oben im Visual Studio-Fenster verwenden.

![Menü „Feedback senden“ in Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Nächste Schritte

Wir haben uns nur einige der Features von Visual Studio angesehen, um uns mit der Benutzeroberfläche vertraut zu machen. Weitere mögliche Schritte:

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über den Code-Editor](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Siehe auch

- [Übersicht der Visual Studio-IDE](../get-started/visual-studio-ide.md)
- [Weitere Features von Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Ändern von Design und Schriftfarben](../ide/quickstart-personalize-the-ide.md)
