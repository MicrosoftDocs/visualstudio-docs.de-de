---
title: 'Tutorial: Öffnen eines Projekts aus einem Repository in Visual Studio 2019'
description: Hier erfahren Sie, wie Sie ein Projekt mithilfe von Visual Studio 2019 in einem Git- oder Azure DevOps-Repository öffnen.
ms.custom: get-started
ms.date: 02/11/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: 5a637b2536c05e8f5678989f47dba61cd6ec7381
ms.sourcegitcommit: 15109ead7991f52092502518a6f4d9061cc22cd2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "100335470"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Öffnen eines Projekts von einem Repository aus

In diesem Tutorial verwenden Sie Visual Studio, um erstmalig eine Verbindung mit einem Repository herzustellen und dann ein Projekt darin zu öffnen.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

## <a name="open-a-project-from-a-github-repo"></a>Öffnen eines Projekts von einem GitHub-Repository aus

Auf welche Weise Sie Projekte aus einem GitHub-Repository mithilfe von Visual Studio 2019 öffnen können, hängt von der Version ab, die Sie verwenden. Insbesondere für [**Version 16.8**](/visualstudio/releases/2019/release-notes/) oder höher stehen Ihnen neue, umfassender integrierte [Git-Funktionen in Visual Studio](../ide/git-with-visual-studio.md) zur Verfügung.

Aber unabhängig davon, welche Version Sie installiert haben, können Sie Projekte aus einem GitHub-Repository immer mit Visual Studio öffnen.

#### <a name="168-and-later"></a>[16.8 und höher](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonen eines GitHub-Repositorys und anschließendes Öffnen eines Projekts

1. Öffnen Sie Visual Studio 2019.

1. Klicken Sie im Startfenster auf **Repository klonen**.

   ![Screenshot des Dialogfelds „Repository klonen“ in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/clone-repository.png)

1. Geben Sie den Speicherort des Repositorys ein, und klicken Sie auf **Klonen**.

   ![Screenshot des Dialogfelds „Repository klonen“ in Visual Studio 2019, Version 16.8 und höher, in das Sie die URL zu einem Git-Repository eingeben](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Sie werden möglicherweise im Dialogfeld **Git-Benutzerinformationen** darum gebeten, Ihre Anmeldedaten einzugeben. Sie können entweder Ihre Daten hinzufügen oder die bereitgestellten Standarddaten bearbeiten.

   ![Screenshot des Dialogfelds „Git-Benutzerinformationen“ in Visual Studio 2019, Version 16.8 und höher, in das Sie Ihre Kontoinformationen eingeben oder in dem Sie diese bearbeiten](../ide/media/vs-2019/git-user-information-dialog.png)

    Klicken Sie auf **Speichern**, um die Informationen ihrer globalen GITCONFIG-Datei hinzuzufügen. Sie können dies auch auf einen späteren Zeitpunkt verschieben, indem Sie auf **Abbrechen** klicken.

    Anschließend lädt Visual Studio automatisch die Projektmappe aus dem Repository und öffnet sie.

   ![Screenshot eines Projekts in Git, das im Projektmappen-Explorer in Visual Studio 2019, Version 16.8 und höher, geöffnet ist](../ide/media/vs-2019/git-solution-explorer.png )

1. Wenn Ihr Repository mehrere Projektmappen enthält, werden diese im Projektmappen-Explorer angezeigt. Sie können die Liste der Projektmappen abrufen, indem Sie im Projektmappen-Explorer auf die Schaltfläche **Darstellung wechseln** klicken.

   ![Screenshot eines Projekts in Git, das im Projektmappen-Explorer in Visual Studio 2019, Version 16.8 und höher, geöffnet ist und bei dem die Schaltfläche „Darstellung wechseln“ hervorgehoben ist](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Im Projektmappen-Explorer haben Sie dann die Möglichkeit, das Stammverzeichnis in der **Ordneransicht** zu öffnen oder eine Projektmappendatei auszuwählen, die geöffnet werden soll.

   ![Screenshot einer SLN-Datei in Git, die im Projektmappen-Explorer geöffnet ist, nachdem Sie in Visual Studio 2019, Version 16.8 und höher auf die Schaltfläche „Darstellung wechseln“ geklickt haben](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Klicken Sie noch einmal auf die Schaltfläche **Darstellung wechseln**, um die Darstellung zu wechseln.

    > [!TIP]
    > Sie können auch das **Git**-Menü in der Visual Studio-IDE verwenden, um ein Repository zu klonen und ein Projekt zu öffnen.
    >
    > ![Screenshot des Git-Menüs in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Lokales Öffnen eines Projekts aus einem zuvor geklonten GitHub-Repository

1. Öffnen Sie Visual Studio 2019.

1. Klicken Sie im Startfenster auf **Projekt oder Projektmappe öffnen**.

    Dann öffnet Visual Studio eine Instanz des Datei-Explorers, in der Sie die Projektmappe oder das Projekt suchen und öffnen können.

   ![Screenshot des Fensters „Projekt oder Projektmappe öffnen“ in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Wenn Sie das Projekt oder die Projektmappe vor Kurzem geöffnet haben, wählen Sie sie im Abschnitt **Zuletzt verwendete öffnen** aus, um sie direkt noch einmal zu öffnen.

    > [!TIP]
    > Sie können auch das **Git**-Menü in der Visual Studio-IDE verwenden, um lokale Ordner und Dateien aus einem Repository zu öffnen, das Sie zuvor geklont haben.
    >
    > ![Screenshot des Git-Menüs in Visual Studio 2019, Version 16.8 und höher, in dem die Option „Local Repositories“ (Lokale Repositorys) erweitert ist](../ide/media/vs-2019/git-menu-local-repositories.png)

    Legen Sie los!

#### <a name="167-and-earlier"></a>[16.7 und niedriger](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonen eines GitHub-Repositorys und anschließendes Öffnen eines Projekts

1. Öffnen Sie Visual Studio 2019.

1. Klicken Sie im Startfenster auf **Code klonen oder auschecken**.

   ![Screenshot des Fensters „Neues Projekt erstellen“ in Visual Studio 2019, Version 16.7 und niedriger](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Geben Sie den Speicherort des Repositorys ein, und klicken Sie auf **Klonen**.

   ![Screenshot des Fensters „Code klonen oder auschecken“ in Visual Studio 2019, Version 16.7 und niedriger](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio öffnet das Projekt aus dem Repository.

1. Ist eine Projektmappendatei verfügbar, wird sie im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wenn Sie auf diese klicken, öffnet Visual Studio die Projektmappe.

   ![Screenshot der Dropdownliste „Projektmappen-Explorer“ in Visual Studio 2019, Version 16.7 und niedriger](./media/open-proj-repo-github-solutions-folders-picker.png)

   Enthält das Repository keine Projektmappendatei (genauer gesagt keine SLN-Datei), wird im Flyoutmenü die Meldung „Keine Projektmappen gefunden“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

    Legen Sie los!

---

> [!NOTE]
> Weitere für Visual Studio 2017 spezifische Informationen finden Sie auf der Seite [Öffnen eines Projekts aus einem Repository in Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md).

## <a name="connect-to-an-azure-devops-server"></a>Herstellen einer Verbindung mit einem Azure DevOps-Server

Was Sie sehen, wenn Sie mithilfe von Visual Studio 2019 eine Verbindung mit einem Azure DevOps-Server herstellen, hängt von der verwendeten Version ab. Insbesondere für [**Version 16.8**](/visualstudio/releases/2019/release-notes/) oder höher haben wir die Benutzeroberfläche geändert, sodass Ihnen neue, umfassender integrierte [Git-Funktionen in Visual Studio](../ide/git-with-visual-studio.md) zur Verfügung stehen.

Unabhängig davon, welche Version Sie installiert haben, können Sie mithilfe von Visual Studio jederzeit eine Verbindung mit einem Azure DevOps-Server herstellen.

#### <a name="168-and-later"></a>[16.8 und höher](#tab/vs168later)

1. Öffnen Sie Visual Studio 2019.

1. Klicken Sie im Startfenster auf **Repository klonen**.

   ![Screenshot des Dialogfelds „Repository klonen“ in Visual Studio 2019, Version 16.8 und höher für Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Klicken Sie im Abschnitt **Repository durchsuchen** auf **Azure DevOps**.

    ![Screenshot des Abschnitts „Repository durchsuchen“ im Dialogfeld „Verbindung mit einem Projekt herstellen“ in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Melden Sie sich mit Ihrem Konto an, wenn ein Anmeldefenster angezeigt wird.

1. Klicken Sie im Dialogfeld **Verbindung mit einem Projekt herstellen** erst auf das Repository, mit dem Sie eine Verbindung herstellen möchten, und anschließend auf **Klonen**.

      ![Screenshot des Dialogfelds „Verbindung mit einem Projekt herstellen“ in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Wenn keine vorausgefüllte Liste der Repositorys angezeigt wird, mit denen eine Verbindung hergestellt werden soll, klicken Sie auf **Azure DevOps Server hinzufügen**, um eine Server-URL einzugeben. Alternativ wird Ihnen möglicherweise die Eingabeaufforderung „Keine Server gefunden“ angezeigt, die Links zum Hinzufügen eines vorhandener Azure DevOps Server-Instanz oder zum Erstellen eines Azure DevOps-Kontos enthält.

   Im nächsten Schritt öffnet Visual Studio den **Projektmappen-Explorer**, in dem die Ordner und Dateien angezeigt werden.

1. Wählen Sie die Registerkarte **Team Explorer** aus, damit die Azure DevOps-Aktionen angezeigt werden.

      ![Screenshot des Dialogfelds „Team Explorer“ in Visual Studio 2019, Version 16.8 und höher](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 und niedriger](#tab/vs167earlier)

1. Öffnen Sie Visual Studio 2019.

1. Klicken Sie im Startfenster auf **Code klonen oder auschecken**.

   ![Screenshot des Fensters „Neues Projekt erstellen“ in Visual Studio 2019, Version 16.7 und niedriger](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Klicken Sie im Abschnitt **Repository durchsuchen** auf **Azure DevOps**.

   ![Screenshot des Fensters „Code klonen oder auschecken“ mit dem Abschnitt „Repository durchsuchen“, in dem Azure DevOps in Visual Studio 2019, Version 16.7 und niedriger aufgeführt wird](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Melden Sie sich mit Ihrem Konto an, wenn ein Anmeldefenster angezeigt wird.

1. Klicken Sie im Dialogfeld **Verbindung mit einem Projekt herstellen** erst auf das Repository, mit dem Sie eine Verbindung herstellen möchten, und anschließend auf **Klonen**.

      ![Screenshot des Dialogfelds „Verbindung mit einem Projekt herstellen“ in Visual Studio 2019, Version 16.7 und niedriger](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Die im Listenfeld angezeigten Elemente hängen von den Azure DevOps-Repositorys ab, auf die Sie Zugriff haben.

   Nach Abschluss des Klonvorgangs öffnet Visual Studio den **Team Explorer** und eine Benachrichtigung wird angezeigt.

     ![Screenshot des Fensters „Team Explorer“ in Visual Studio 2019, Version 16.7 und niedriger, nachdem der Klonvorgang abgeschlossen ist](./media/vs-2019/clone-complete-azure-devops.png)

1. Klicken Sie auf den Link **Ordneransicht anzeigen**, damit Ihre Ordner und Dateien angezeigt werden.

     ![Screenshot des Abschnitts „Projektmappen“ im Fenster „Team Explorer“ in Visual Studio 2019, Version 16.7 und niedriger, nachdem der Klonvorgang abgeschlossen ist](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio öffnet den **Projektmappen-Explorer**.

1. Klicken Sie auf den Link **Projektmappen und Ordner**, um nach einer Projektmappendatei (d. h. einer SLN-Datei) zu suchen, die geöffnet werden soll.

      ![Screenshot der Benachrichtigung „Projektmappen und Ordner“ vom Team Explorer in Visual Studio 2019, Version 16.7 und niedriger](./media/open-proj-repo-solutions-folders.png)

   Wenn Ihr Repository keine Projektmappendatei enthält, wird die Meldung „Keine Projektmappen gefunden“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

---

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit dem Codieren mit Visual Studio loslegen möchten, können Sie sich die ausführlichen Informationen in einem der folgenden sprachspezifischen Tutorials ansehen:

- [Visual Studio-Tutorials | **C#**](./csharp/index.yml)
- [Visual Studio-Tutorials | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio | **Python**](../python/index.yml)
- [Visual Studio | **JavaScript**, **TypeScript** und **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Siehe auch

- [Öffnen eines Projekts aus einem Repository in Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Neue Git-Funktionen in Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Erste Schritte mit Azure Repos und Visual Studio)
- [Microsoft Learn: Get started with Azure DevOps](/learn/modules/get-started-with-devops/) (Microsoft Learn: Erste Schritte mit Azure DevOps)