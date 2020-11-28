---
title: Herstellen einer Verbindung mit Projekten in Team Explorer
description: Erfahren Sie, wie Sie Team Explorer in Visual Studio verwenden können, um mit Teammitgliedern gemeinsam Projekte zu entwickeln und zu verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: fd482bd2225025b5cd8a14f0387e938626fad6d5
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006314"
---
# <a name="connect-to-projects-in-team-explorer"></a>Herstellen einer Verbindung mit Projekten in Team Explorer

::: moniker range="vs-2017"

Verwenden Sie das Toolfenster **Team Explorer**, um Ihren Codeaufwand für die Entwicklung eines Projekts mit anderen Teammitgliedern zu koordinieren und die Aufgaben zu verwalten, die Ihnen, Ihrem Team oder Ihren Projekten zugewiesen sind. **Team Explorer** verbindet Visual Studio mit Git- und GitHub-Repositorys, Repositorys der Team Foundation-Versionskontrolle (TFVC) und Projekten, die auf [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) oder einer lokalen [Azure DevOps Server](/azure/devops/index-all)-Instanz (früher „TFS“ genannt) gehostet werden. Sie können Quellcode, Arbeitselemente und Builds verwalten.

::: moniker-end

::: moniker range="vs-2019"

Sie können mit dem Toolfenster **Team Explorer** Ihren Codeaufwand für die Entwicklung eines Projekts mit anderen Teammitgliedern koordinieren und die Aufgaben verwalten, die Ihnen, Ihrem Team oder Ihren Projekten zugewiesen sind.

> [!IMPORTANT]
> Mit dem neuesten Release von Visual Studio 2019, [Version 16.8](/visualstudio/releases/2019/release-notes/), ist die neue Git-Versionskontrolle jetzt standardmäßig aktiviert. Wenn Sie jedoch weiterhin Team Explorer verwenden möchten, wechseln Sie zu **Extras** > **Optionen** > **Umgebung** > **Vorschaufeatures**, und aktivieren Sie das Kontrollkästchen **Neue Git-Benutzeroberfläche**. Weitere Informationen finden Sie auf der Seite [Git-Benutzeroberfläche in Visual Studio](git-with-visual-studio.md).

**Team Explorer** verbindet Visual Studio mit Git- und GitHub-Repositorys, Repositorys der Team Foundation-Versionskontrolle (TFVC) und Projekten, die auf [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) oder einer lokalen [Azure DevOps Server](/azure/devops/index-all)-Instanz (früher „TFS“ genannt) gehostet werden. Sie können Quellcode, Arbeitselemente und Builds verwalten.

::: moniker-end

![Team Explorer-Homepage in Visual Studio](media/team-explorer/team-explorer.png "Der Team Explorer: Startseite in Visual Studio.")

::: moniker range="vs-2017"

> [!TIP]
> Wenn Sie Visual Studio öffnen und **Team Explorer** nicht angezeigt wird, öffnen Sie das Plug-In, indem Sie in der Menüleiste auf **Ansicht** > **Team Explorer** klicken oder **STRG**+ **&#92;** , **STRG**+**M** drücken.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Herstellen einer Verbindung mit einem Projekt oder Repository

Über die Seite **Verbinden** können Sie eine Verbindung mit einem Projekt oder Repository herstellen.

![Seite „Verbinden“ in Team Explorer](media/team-explorer/connect.png "Der Team Explorer: Seite „Verbinden“ in Visual Studio.")

So stellen Sie eine Verbindung mit einem Projekt her:

1. Öffnen Sie die Seite **Verbinden**, indem Sie auf das Symbol **Verbindungen verwalten** klicken.

   ![Schaltfläche „Verbindungen verwalten“ in Team Explorer](media/team-explorer/manage-connections.png "Der Team Explorer: Schaltfläche „Verbindungen verwalten“ in Visual Studio.")

1. Klicken Sie auf der Seite **Verbinden** auf **Verbindungen verwalten** > **Verbindung mit einem Projekt herstellen**.

   ![Herstellen einer Verbindung mit einem Projekt in Team Explorer](media/team-explorer/connect-project.png "Der Team Explorer: Option „Verbindung mit einem Projekt herstellen“ in Visual Studio.")

> [!TIP]
> Wenn Sie ein Projekt aus einem Repository öffnen möchten, finden Sie weitere Informationen unter [Öffnen eines Projekts von einem Repository aus](../get-started/tutorial-open-project-from-repo.md). Informationen dazu, wie Sie ein neues Projekt erstellen oder Benutzer zu einem Projekt hinzufügen, finden Sie unter [Erstellen eines Projekts (Azure DevOps)](/azure/devops/organizations/projects/create-project) und [Hinzufügen von Benutzern zu einem Projekt oder Team (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Siehe auch

- [Git-Benutzeroberfläche in Visual Studio](git-with-visual-studio.md)
- [Tutorial: Öffnen eines Projekts von einem Repository aus](../get-started/tutorial-open-project-from-repo.md)
- [Team Explorer reference (Referenz für Team Explorer)](reference/team-explorer-reference.md)
- [Connect to a project (Azure DevOps) (Herstellen einer Verbindung mit einem Projekt in Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Behandeln von Problemen beim Herstellen einer Verbindung mit einem Projekt](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
