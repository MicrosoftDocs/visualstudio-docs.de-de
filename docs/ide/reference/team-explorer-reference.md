---
title: Team Explorer-Referenz
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: fa73894d713ded42696f5e47d40dffb2d2405b1a
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928081"
---
# <a name="team-explorer-reference"></a>Team Explorer-Referenz

In diesem Artikel sind Links zu Azure DevOps-Artikeln über verschiedene Funktionen in **Team Explorer** enthalten.

Verwenden Sie das Toolfenster **Team Explorer**, um Ihren Codeaufwand für die Entwicklung eines Projekts mit anderen Teammitgliedern zu koordinieren und die Aufgaben zu verwalten, die Ihnen, Ihrem Team oder Ihren Projekten zugewiesen sind. **Team Explorer** verbindet Visual Studio mit Git- und GitHub-Repositorys, Repositorys der Team Foundation-Versionskontrolle (TFVC) und Projekten, die auf [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) oder einer lokalen [Azure DevOps Server](/azure/devops/index-all)-Instanz (früher „TFS“ genannt) gehostet werden. Sie können Quellcode, Arbeitselemente und Builds verwalten.

## <a name="home-page"></a>Homepage

Nach dem [Herstellen einer Verbindung mit einem Projekt](../connect-team-project.md) in **Team Explorer** stehen Ihnen folgende Links im Abschnitt **Projekt** zur Verfügung:

- [Clone repository (Klonen eines Repositorys)](/azure/devops/repos/git/clone)
- [Web Portal (Webportal)](/azure/devops/project/navigation/index)
- [Task Board](/azure/devops/boards/sprints/task-board)

Die **Homepage** weist abhängig davon, ob Sie eine Verbindung mit einem [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true)- oder [TFVC](/azure/devops/repos/tfvc/overview)-Repository (Team Foundation-Versionskontrolle) hergestellt haben, verschiedene Funktionen auf.

> [!TIP]
> Einen Vergleich der zwei Versionskontrollsysteme finden Sie unter [Choose the right version control for your project (Azure DevOps) (Auswählen der passenden Versionskontrolle für Ihr Projekt (Azure DevOps))](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Homepage** mit Git | **Homepage** mit TFVC |
| - | - |
| ![Team Explorer-Homepage mit Git in Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Team Explorer-Homepage mit TFVC in Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Seite „Änderungen“ (Git)

Siehe [Save work with commits (Speichern des Fortschritts mit Commits)](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Seite „Branches“ (Git)

Siehe [Create work in branches (Arbeiten mit Branches)](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Seite „Pull Requests“ (Git)

Siehe [Review code with pull requests (Überprüfen von Code mit Pull Requests)](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Seite „Synchronisieren“ (Git)

Siehe [Update code with fetch and pull (Aktualisieren von Code mit Fetch und Pull)](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Seite „Tags“ (Git)

Siehe [Work with Git tags (Verwenden von Git-Tags)](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Seite „Meine Arbeit“ (TFVC)

Siehe [Suspend/resume work (Anhalten/Fortsetzen der Arbeit)](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) und [Code review (Code Review)](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Seite „Ausstehende Änderungen“ (TFVC)

Siehe [Manage pending changes (Verwalten ausstehender Änderungen)](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Find shelvesets (Suchen von Shelvesets)](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets), and [Resolve conflicts (Lösen von Konflikten)](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Seite „Quellcodeverwaltungs-Explorer“ (TFVC)

Siehe [Add/view files and folders (Hinzufügen und Anzeigen von Dateien und Ordnern)](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Seite „Arbeitselemente“

Mit der Seite **Arbeitselemente** können Sie Abfragen von [Arbeitselementen](/azure/devops/boards/work-items/about-work-items) anzeigen. Thema

- [Add work items (Hinzufügen von Arbeitselementen)](/azure/devops/boards/backlogs/add-work-items)
- [Use the query editor to list and manage queries (Verwenden des Abfrage-Editors zum Auflisten und Verwalten von Abfragen)](/azure/devops/boards/queries/using-queries)
- [Organize query folders and set query permissions (Sortieren von Abfrageordnern und Festlegen von Abfrageberechtigungen)](/azure/devops/boards/queries/set-query-permissions)
- [Open query in Excel (Öffnen von Abfragen in Excel)](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Open query in Project (Öffnen von Abfragen im Projekt)](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Email query results list using Outlook (Senden der Abfrageergebnisliste per E-Mail mit Outlook)](/azure/devops/boards/queries/share-plans)
- [Create reports from query in Excel (Erstellen von Berichten aus Abfragen in Excel)](/azure/devops/report/excel/create-status-and-trend-excel-reports) (nur TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> In Visual Studio 2019 gibt es eine neue [Arbeitselementfunktion](/azure/devops/boards/work-items/set-work-item-experience-vs). Weitere Informationen zum Anzeigen von Arbeitselementen in Visual Studio 2019 finden Sie unter [View and add work items (Anzeigen und Hinzufügen von Arbeitselementen)](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Seite „Builds“

Mit der Seite **Builds** können Sie die Builddefinitionen für das Projekt anzeigen.

Thema

- [Create build pipelines (Erstellen von Buildpipelines)](/azure/devops/pipelines/tasks/index)
- [View and manage builds (Anzeigen und Verwalten von Builds)](/azure/devops/pipelines/overview)
- [Manage the build queue (Verwalten der Buildwarteschlange)](/azure/devops/pipelines/agents/pools-queues)
- [Install continuous delivery (CD) tools for Visual Studio (Installieren von Continuous Delivery-Tools für Visual Studio)](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Configure and execute continuous delivery (CD) for your app (Konfigurieren und Ausführen von Continuous Delivery für Ihre App)](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Seite "Einstellungen"

Auf der Seite **Einstellungen** können Sie Verwaltungsfunktionen entweder für ein Teamprojekt oder eine Teamprojektsammlung konfigurieren. Weitere Informationen finden Sie in den folgenden Artikeln:

| Projekt | Projektsammlung | Andere |
| - | - | - |
| [Security, Group Membership (Sicherheit: Gruppenmitgliedschaft)](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Security, Source Control (TFVC) (Sicherheit: Quellcodeverwaltung (TFVC))](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Work Item Areas (Arbeitselementbereiche)](/azure/devops/organizations/settings/set-area-paths)<br/>[Work Item Iterations (Arbeitselementiterationen)](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Portal Settings (Portaleinstellungen)](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Project Alerts (Projektwarnungen)](/azure/devops/notifications/howto-manage-team-notifications) | [Security, Group Membership (Sicherheit: Gruppenmitgliedschaft)](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Source Control (TFVC) (Quellcodeverwaltung (TFVC))](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Process Template Manager (Prozessvorlagen-Manager)](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git Global Settings (Globale Git-Einstellungen)](/azure/devops/repos/git/git-config)<br/>[Git Repository Settings (Git-Repositoryeinstellungen)](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Weitere Informationen

- [Connect to projects in Team Explorer (Herstellen einer Verbindung mit Projekten in Team Explorer)](../../ide/connect-team-project.md)