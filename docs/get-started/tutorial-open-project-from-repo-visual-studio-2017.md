---
title: 'Tutorial: Öffnen eines Projekts aus einem Repository in Visual Studio 2017'
description: Hier erfahren Sie, wie Sie ein Projekt mithilfe von Visual Studio 2017 in einem Git- oder Azure DevOps-Repository öffnen.
ms.custom: get-started
ms.date: 01/25/2021
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
monikerRange: vs-2017
ms.openlocfilehash: 97bfe7178d3bd744d1e441f8428cd38e8241b721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951926"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Tutorial: Öffnen eines Projekts aus einem Repository in Visual Studio 2017

In diesem Tutorial verwenden Sie Visual Studio 2017, um erstmalig eine Verbindung mit einem Repository herzustellen und dann ein Projekt darin zu öffnen.

> [!TIP]
> Es gibt eine neue, vollständig integrierte Möglichkeit zum Herstellen einer Verbindung mit einem GitHub-Repository in [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Weitere Informationen finden Sie auf der Seite [**Neue Git-Funktionen in Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Öffnen eines Projekts aus einem GitHub-Repository mithilfe von Visual Studio 2017

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen**.

   Der Bereich **Team Explorer – Verbinden** wird geöffnet.

    ![Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-team-explorer.png)

1. Klicken Sie im Abschnitt **Lokale Git-Repositorys** auf **Klonen**.

    ![Auswählen von „Klonen“ im Abschnitt „Lokale Git-Repositorys“](./media/open-proj-repo-local-git-repo-clone.png)

1. Geben oder fügen Sie die URL Ihres Repositorys in das Feld ***Geben Sie die URL eines zu klonenden Git ein** _ ein, und drücken Sie dann die _*EINGABETASTE**. (Melden Sie sich im Falle einer entsprechenden Aufforderung bei GitHub an.)

   Nach dem Klonen Ihres Repositorys durch Visual Studio wird Team Explorer geschlossen und der Projektmappen-Explorer geöffnet. Die Meldung *Klicken Sie oben auf "Projektmappen und Ordner", um eine Liste mit Projektmappen anzuzeigen.* wird angezeigt. Wählen Sie **Projektmappen und Ordner** aus.

   ![Auswählen von „Projektmappen und Ordner“ im Projektmappen-Explorer](./media/open-proj-repo-github-solutions-folders.png)

1. Ist eine Projektmappendatei verfügbar, wird sie im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wählen Sie sie aus, und Visual Studio öffnet die Projektmappe.

   ![Auswählen des gewünschten Elements in der Dropdownliste des Projektmappen-Explorers](./media/open-proj-repo-github-solutions-folders-picker.png)

   Enthält das Repository keine Projektmappendatei (insbesondere eine SLN-Datei), wird im Flyoutmenü „Keine Projektmappen gefunden.“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

### <a name="review-your-work"></a>Überprüfen Ihrer Arbeit

Sehen Sie sich die folgende Animation an, um Ihre Arbeit zu überprüfen, die Sie im Rahmen des vorherigen Abschnitts verrichtet haben.

   ![Animation zum Öffnen eines Projekts in einem GitHub-Repository mithilfe von Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Öffnen eines Projekts aus einem Azure DevOps-Repository mithilfe von Visual Studio 2017

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen**.

   Der Bereich **Team Explorer – Verbinden** wird geöffnet.

    ![Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-team-explorer.png)

1. Es gibt zwei Möglichkeiten zum Herstellen einer Verbindung mit dem Azure DevOps-Repository:

      - Klicken Sie im Abschnitt **Anbieter für gehostete Dienste** auf **Verbinden...** .

        ![Abschnitt „Anbieter für gehostete Dienste“ im Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-azure-devops.png)

      - Klicken Sie in der Dropdownliste **Verbindungen verwalten** auf **Verbindung mit einem Projekt herstellen...** .

        ![Abschnitt „Verbindungen verwalten“ im Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Klicken Sie im Dialogfeld **Verbindung mit einem Projekt herstellen** erst auf das Repository, mit dem Sie eine Verbindung herstellen möchten, und anschließend auf **Klonen**.

      ![Dialogfeld „Verbindung mit einem Projekt herstellen“ in Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Die im Listenfeld angezeigten Elemente hängen von den Azure DevOps-Repositorys ab, auf die Sie Zugriff haben.

1. Nach dem Klonen Ihres Repositorys durch Visual Studio wird Team Explorer geschlossen und der Projektmappen-Explorer geöffnet. Die Meldung *Klicken Sie oben auf "Projektmappen und Ordner", um eine Liste mit Projektmappen anzuzeigen.* wird angezeigt. Wählen Sie **Projektmappen und Ordner** aus.

      ![Benachrichtigung „Projektmappen und Ordner“ im Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Eine Projektmappendatei (insbesondere eine SLN-Datei) wird im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wählen Sie sie aus, und Visual Studio öffnet die Projektmappe.

   Enthält das Repository keine Projektmappendatei, wird im Flyoutmenü „Keine Projektmappen gefunden.“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit dem Programmieren mit Visual Studio 2017 loslegen möchten, erhalten Sie in den folgenden sprachspezifischen Tutorials weitere Informationen:

- [Visual Studio-Tutorials | **C#**](./csharp/index.yml)
- [Visual Studio-Tutorials | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio | **Python**](../python/index.yml)
- [Visual Studio | **JavaScript**, **TypeScript** und **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Siehe auch

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Erste Schritte mit Azure Repos und Visual Studio)
- [Microsoft Learn: Get started with Azure DevOps](/learn/modules/get-started-with-devops/) (Microsoft Learn: Erste Schritte mit Azure DevOps)
- [Neue Git-Funktionen in Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
