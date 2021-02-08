---
title: Erstellen eines Azure-Clouddienstprojekts
description: Erfahren Sie, wie Sie ein Azure-Clouddienstprojekt mit Visual Studio erstellen.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: d652172bde2ecd3aea4bb027e46173eaa5fe7b17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844501"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Erstellen eines Azure-Clouddienstprojekts mit Visual Studio

Visual Studio stellt eine Projektvorlage bereit, mit der Sie einen [Azure-clouddienst](/azure/cloud-services/cloud-services-choose-me)erstellen können, bei dem es sich um einen einfachen, allgemeinen Azure-Dienst handelt. Nach der Erstellung des Projekts können Sie den Clouddienst mit Visual Studio in Azure konfigurieren, debuggen und bereitstellen.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Schritte zum Erstellen eines Azure-Clouddienstprojekts in Visual Studio
In diesem Abschnitt wird das Erstellen eines Azure-Clouddienstprojekts in Visual Studio mit einem oder mehreren Webrollen erläutert.

::: moniker range="vs-2017"
1. Öffnen Sie Visual Studio als Administrator.

1. Wählen Sie im Hauptmenü die Optionen **Datei** > **Neu** > **Projekt** aus.

1. Wählen Sie **Cloud** in den Projektvorlagenknoten „Visual C#“ oder „Visual Basic“ und dann **Azure-Clouddienst** in der Liste der Vorlagen aus.

    ![Neuer Azure-Clouddienst](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Geben Sie an, mit welcher Version von .NET Framework Sie das Projekt entwickeln möchten.

1. Geben Sie einen Namen und Speicherort für das Projekt und einen Namen für die Projektmappe ein.

1. Klicken Sie auf **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

1. Geben Sie im Suchfeld *Cloud* ein, und wählen Sie dann **Azure-Clouddienst** aus.

   ![Neuer Azure-Clouddienst](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Benennen Sie das Projekt, und klicken Sie auf **Erstellen**.

   ![Benennen Sie das Projekt.](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. Wählen Sie im Dialogfeld **Neuer Clouddienst** die Rollen aus, die Sie hinzufügen möchten, und klicken Sie auf die Schaltfläche mit dem Pfeil nach rechts, um sie der Projektmappe hinzuzufügen.

    ![Auswählen neuer Azure-Clouddienstrollen](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Um eine Rolle umzubenennen, die Sie hinzugefügt haben, zeigen Sie im Dialogfeld **Neuer Clouddienst** mit dem Mauszeiger auf die Rolle, und wählen Sie im Kontextmenü die Option **Umbenennen** aus. Sie können eine Rolle auch in der Projektmappe umbenennen (im **Projektmappen-Explorer**), nachdem sie hinzugefügt wurde.

    ![Umbenennen einer Azure Clouddienstrolle](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Das Visual Studio-Azure-Projekt weist Zuordnungen zu den Rollenprojekten in der Projektmappe auf. Das Projekt enthält zudem die *Dienstdefinitionsdatei* und die *Dienstkonfigurationsdatei*:

- **Dienstdefinitionsdatei:** Definiert die Laufzeiteinstellungen für Ihre Anwendung wie etwa erforderliche Rollen, Endpunkte und Größe des virtuellen Computers.
- **Dienstkonfigurationsdatei:** Konfiguriert, wie viele Instanzen einer Rolle ausgeführt werden, und die Werte der für eine Rolle definierten Einstellungen.

Weitere Informationen zu diesen Dateien finden Sie unter [Konfigurieren der Rollen für einen Azure-clouddienst mit Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Nächste Schritte
- [Verwalten von Rollen in Azure-Clouddienstprojekten mit Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
