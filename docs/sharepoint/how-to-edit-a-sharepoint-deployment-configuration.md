---
title: 'Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungs Konfiguration | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine SharePoint-Bereitstellungs Konfiguration erstellen oder eine vorhandene Bereitstellungs Konfiguration ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e64f805496d03b42ca70489bab1302ecf58b33bc
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903558"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungs Konfiguration
  Sie können eine Bereitstellungs Konfiguration erstellen oder eine vorhandene Bereitstellungs Konfiguration ändern. Beispielsweise können Sie einen einzelnen Schritt ausführen oder die Reihenfolge der Schritte im Bereitstellungs Prozess ändern. Möglicherweise möchten Sie Bereitstellungs Konfigurationen erstellen oder ändern, da die integrierten und Programm gesteuert hinzugefügten Konfigurationen nicht geändert werden können.

## <a name="create-a-sharepoint-deployment-configuration"></a>Erstellen einer SharePoint-Bereitstellungs Konfiguration

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>So erstellen Sie eine SharePoint-Bereitstellungs Konfiguration

1. Wählen Sie in **Projektmappen-Explorer** ein SharePoint-Projekt aus, und wählen Sie dann in der Menüleiste **Projekt, Projekt** _Name_**Eigenschaften** aus.

2. Wählen Sie auf der Registerkarte **SharePoint** die Schaltfläche **neu** aus.

     Das Dialogfeld **Neue Bereitstellungs Konfiguration hinzufügen** wird angezeigt.

3. Geben Sie im Textfeld **Name** einen Namen für die Bereitstellungs Konfiguration ein.

4. Wählen Sie im Bereich **Verfügbare Bereitstellungs Schritte** die Schritte aus, die Sie der Bereitstellungs Konfiguration hinzufügen möchten, klicken Sie auf die **>** Schaltfläche (), und klicken Sie dann auf die Schaltfläche **OK** .

    > [!NOTE]
    > Wenn Sie einen Befehl vor der Bereitstellung oder einen Befehl nach der Bereitstellung konfiguriert haben, werden diese Schritte nur ausgeführt, wenn Sie Sie einer angepassten Bereitstellungs Konfiguration hinzufügen.

## <a name="change-the-active-deployment-configuration"></a>Ändern der aktiven Bereitstellungs Konfiguration

#### <a name="to-change-the-active-deployment-configuration"></a>So ändern Sie die aktive Bereitstellungs Konfiguration

1. Wählen Sie in **Projektmappen-Explorer** ein SharePoint-Projekt aus, und wählen Sie dann in der Menüleiste die Option **Projekt**  >  **\<*ProjectName*> Eigenschaften** aus.

2. Wählen Sie die Registerkarte **SharePoint** aus.

3. Wählen Sie im Listenfeld **aktive Bereitstellungs Konfiguration** den Namen der Bereitstellungs Konfiguration aus, die Sie verwenden möchten.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
