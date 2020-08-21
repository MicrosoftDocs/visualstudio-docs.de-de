---
title: Visual Studio-Installer Projekte und .net Core 3,1
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c35e6a12262083d09575b51f6c9f918ba30a27b1
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714389"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Erweiterung für Visual Studio-Installer Projekte und .net Core 3,1

Das Verpacken von Anwendungen als MSI wird häufig mithilfe der Erweiterung "Visual Studio-Installer Projects" durchgeführt.

Sie können die Erweiterung hier herunterladen: [Visual Studio-Installer Projekte](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Update für .net Core
.Net Core verfügt über zwei verschiedene Modelle für die Veröffentlichung.

- Framework-abhängige bereit Stellungen

- In eigenständigen Anwendungen ist die Laufzeit enthalten.

Weitere Informationen zu diesen Bereitstellungs Strategien finden Sie unter [Übersicht über das Veröffentlichen von .net Core-Anwendungen](https://docs.microsoft.com/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Workflow Änderungen für .net Core 3,1

1. Wählen Sie Elemente anstelle der **primären Ausgabe** **veröffentlichen** aus, um die korrekte Ausgabe für .net Core 3,1-Projekte zu erhalten.  Um dieses Dialogfeld anzuzeigen, wählen **Add**Sie  >  im Kontextmenü des Projekts die Option**Projekt Ausgabe hinzufügen...** aus.

    ![Die Ausgabe Gruppe "Elemente veröffentlichen" im Dialogfeld "Projekt Ausgabe Gruppe hinzufügen"](../deployment/media/installer-projects-net-core-publish-items-output.png "Veröffentlichungs Elemente auswählen")

2. Um ein eigenständiges Installationsprogramm zu erstellen, legen Sie die **publishprofilepath** -Eigenschaft für den Knoten **Publish Items** im Setup-Projekt fest, indem Sie den relativen Pfad eines Veröffentlichungs Profils mit den richtigen Eigenschaften festlegen.

    ![Festlegen des Veröffentlichungs Profils für das Veröffentlichungs Element-Projekt Ausgabe Element](../deployment/media/installer-projects-net-core-publish-profile.png "Veröffentlichungs Profil festlegen")

### <a name="prerequisites-for-net-core-31"></a>Voraussetzungen für .net Core 3,1

Wenn Sie möchten, dass das Installationsprogramm die erforderliche Laufzeit für eine Framework-abhängige .net Core 3,1-App installiert, können Sie dies mit den [Voraussetzungen](../deployment/application-deployment-prerequisites.md)tun.  Öffnen Sie im Dialogfeld Eigenschaften des Installationsprogramms das Dialogfeld **Voraussetzungen...** , und die folgenden Einträge werden angezeigt:

![.Net Core-Elemente im Dialogfeld "erforderliche Komponenten"](../deployment/media/installer-projects-net-core-prerequisites.png "Erforderliche Komponenten für .NET Core")

Die **.net Core-Runtime...** -Option sollte für Konsolen Anwendungen, **.net Desktop Runtime..** . ausgewählt werden, sollte für WPF-/WinForms-Anwendungen ausgewählt werden.

>[!NOTE]
>Diese Elemente sind ab der Version Visual Studio 2019 Update 7 vorhanden.

## <a name="see-also"></a>Weitere Informationen

- [Dialogfeld "Erforderliche Komponenten"](../ide/reference/prerequisites-dialog-box.md)
- [Erforderliche Anwendungs Bereitstellungs Voraussetzungen](../deployment/application-deployment-prerequisites.md)