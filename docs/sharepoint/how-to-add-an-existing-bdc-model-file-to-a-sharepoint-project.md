---
title: 'Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie einem SharePoint-Projekt in Visual Studio eine vorhandene BDC-Modelldatei (Business Data Connectivity) hinzu, damit Sie ein BDC-Modell anpassen, Verpacken und erneut bereitstellen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af0768b4834eb1cad3654b6d74ee8f02cf464245
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882673"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>How to: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt
  Sie können ein Business Data Connectivity (BDC)-Modell mithilfe von Visual Studio anpassen, Verpacken und erneut bereitstellen, indem Sie die Modelldatei (*. bdcm*) zu einem SharePoint-Farm Projekt hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>So fügen Sie eine BDC-Modelldatei zu einem SharePoint-Projekt hinzu

1. Wählen Sie in **Projektmappen-Explorer** den Ordner für ein SharePoint-Projekt aus.

2. Wählen Sie in der Menüleiste die Option **Projekt**  >  **Vorhandenes Element hinzufügen** aus.

3. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zum Speicherort der Modell Definitionsdatei, die Sie dem Projekt hinzufügen möchten, wählen Sie die Datei aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

    Wenn das Modell kein Lob- *System (Line of Business) vom Typ .NET-Assembly* definiert, wird das Dialogfeld **.NET-Assembly-LobSystem hinzufügen** geöffnet.

4. Wenn das Dialogfeld angezeigt wird, führen Sie einen der folgenden Schritte aus:

   - Wenn Sie benutzerdefinierten Code schreiben und einen Designer verwenden möchten, um die Metadaten für das importierte Modell zu definieren, klicken Sie auf die Schaltfläche **Ja** , benennen Sie das System, und klicken Sie dann auf die Schaltfläche **OK** .

   - Wählen Sie andernfalls die Schaltfläche **Nein** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Das **Business Data Connectivity-Modell** Element wird dem Projekt hinzugefügt.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [How to: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
