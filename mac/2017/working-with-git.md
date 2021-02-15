---
title: Arbeiten mit Git
description: Verwenden von Git in Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 31e38d728eb3c336b1d3160a920ef18055de1b1f
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616300"
---
# <a name="working-with-git"></a>Arbeiten mit Git

Bei Git handelt es sich um ein verteiltes Versionskontrollsystem, mit dem die Mitglieder eines Teams gleichzeitig an den gleichen Dokumenten arbeiten können. Dies bedeutet, dass es einen zentralen Server mit allen Dateien gibt. Wenn aber ein Repository aus dieser zentralen Quelle ausgecheckt wird, wird das gesamte Repository auf Ihrem lokalen Computer geklont.

In den folgenden Abschnitten wird erläutert, wie Git für die Versionskontrolle in Visual Studio für Mac verwendet werden kann.

## <a name="git-version-control-menu"></a>Git-Menü für die Versionskontrolle

Die folgende Abbildung veranschaulicht die Optionen, die in Visual Studio für Mac vom Menüelement für die Versionskontrolle bereitgestellt werden:

![Menüelement für die Versionskontrolle](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Push und Pull

Push und Pull sind zwei der am häufigsten verwendeten Aktionen in Git. Um die Änderungen anderer am Remoterepository zu synchronisieren, müssen Sie einen **Pull** ausführen. Dazu wählen Sie in Visual Studio für Mac **Versionskontrolle > Update Solution** (Lösung aktualisieren) aus.

Wenn Sie Ihre Dateien aktualisiert, überprüft und sie committet haben, müssen Sie sie anschließend an das Remoterepository **pushen**, damit andere auf Ihre Änderungen zugreifen können. Dazu wählen Sie in Visual Studio für Mac **Versionskontrolle > Änderungen mit Push übertragen** aus. Daraufhin wird das Dialogfeld „Push“ angezeigt, mit dem Sie die ausgecheckten Änderungen anzeigen und den Branch auswählen können, an den die Änderungen gepusht werden sollen:

![Dialogfeld mit dem Branch, auf den committet werden soll](media/version-control-gitPush.png)

Sie können Ihre Änderungen auch gleichzeitig über das Dialogfeld „Commit“ pushen und committen:

![Option für das gleichzeitige Committen und Pushen](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Verantwortung zuweisen, Protokoll und Zusammenführen

Am unteren Rand des Fensters befinden sich die unten dargestellten fünf Registerkarten:

![Registerkarten zur Versionskontrolle](media/version-control-gitTabs.png)

Damit können Sie die folgenden Aktionen ausführen:

* **Quelle**: Zeigt die Quellcodedatei an
* **Änderungen**: Zeigt die Änderung im Code für die lokale Datei und die Basisdatei an. Sie können auch verschiedene Versionen der Datei aus verschiedenen Hashes vergleichen:

    ![Registerkarte mit Änderungen](media/version-control-gitChange.png)

* **Verantwortung zuweisen**: Zeigt den Benutzernamen des Benutzers, der jeden Codeabschnitt zugeordnet.
* **Protokoll**: Zeigt alle Commits, Uhrzeiten, Datumsangaben, Nachrichten und für die Datei verantwortlichen Benutzer an:

    ![Protokollregisterkarte](media/version-control-gitLog.png)

* **Zusammenführen**: Kann bei einem Zusammenführungskonflikt beim Committen Ihrer Arbeit verwendet werden. Damit wird eine visuelle Darstellung der Änderungen angezeigt, die Sie und andere Entwickler vorgenommen haben. So können Sie beide Codeabschnitte sauber kombinieren.

## <a name="switching-branches"></a>Wechseln von Branches

Der erste in einem Repository erstellte Branch wird standardmäßig als **Mainbranch** bezeichnet. Es gibt keine technischen Unterschiede zwischen dem Mainbranch und allen anderen. Der Mainbranch wird aber in Entwicklungsteams am häufigsten als „Live“- oder „Produktionsbranch“ bezeichnet.

Durch das Branchen von Main (oder jedem anderen Branch) kann eine eigenständige Entwicklungslinie erstellt werden. Diese neue Version des Mainbranchs kann unabhängig von der Liveversion bereitgestellt werden. Branches werden in der Softwareentwicklung häufig für Funktionen so verwendet.

Benutzer können für jedes Repository beliebig viele Branches erstellen. Es wird aber empfohlen, einen Branch wieder zu löschen, wenn er nicht mehr gebraucht wird, damit das Repository aufgeräumt bleibt.

Branches können in Visual Studio für Mac unter **Versionskontrolle > Manage Branches and Remotes...** (Branches und Remoteelemente verwalten) angezeigt werden:

![Branchesansicht](media/version-control-gitBranch2.png)

Wechseln Sie zu einem anderen Branch, indem Sie ihn in der Liste auswählen und auf **Zu Branch wechseln** klicken.

Um einen neuen Branch zu erstellen, wählen Sie im Konfigurationsdialog des Git-Repositorys **Neu** aus. Geben Sie den Namen des neuen Branchs ein:

![Neuen Branch erstellen](media/version-control-gitBranch.png)

Sie können auch einen Remotebranch als _Nachverfolgungsbranch_ festlegen. Weitere Informationen zu Nachverfolgungsbranches finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Sehen Sie sich der aktuellen Branch im Projektmappenpad neben dem Projektnamen an:

 ![Aktueller Branch im Projektmappenpad](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Überprüfen und Committen

Um Änderungen in den Dateien zu überprüfen, verwenden Sie die Registerkarten „Änderungen“, „Verantwortung zuweisen“, „Protokoll“ und „Zusammenführen“ für jedes Dokument, wie weiter oben in diesem Thema veranschaulicht.

Überprüfen Sie alle Änderungen in Ihrem Projekt, indem Sie zum Menüelement **Versionskontrolle > Review Solution and Commit** (Lösung und Commit überprüfen) wechseln:

![Codeüberprüfungsansicht](media/version-control-gitReviewCommit.png)

Hiermit können Sie alle Änderungen in jeder Projektdatei mit den Optionen „Revert“ (Wiederherstellen), „Create a Patch“ (Patch erstellen) oder „Commit“ (Commit ausführen) anzeigen.

Wenn Sie eine Datei für ein Remoterepository committen möchten, klicken Sie auf **Commit**, geben Sie eine Commitnachricht ein, und bestätigen Sie mit „Commit“:

![Committen einer Datei](media/version-control-gitCommit.png)

Nachdem Sie die Änderungen committet haben, pushen Sie sie an das Remoterepository, damit andere Benutzer diese sehen können.

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Weitere Informationen

* [Freigeben Ihres Codes mit Visual Studio 2017 und dem Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)