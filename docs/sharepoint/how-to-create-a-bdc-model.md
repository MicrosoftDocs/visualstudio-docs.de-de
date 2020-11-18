---
title: 'Vorgehensweise: Erstellen eines BDC-Modells | Microsoft-Dokumentation'
description: Erstellen Sie ein Business Data Connectivity (BDC)-Modell mithilfe der Visual Studio-Vorlage für diese Art von Element, und fügen Sie das Modell dann einem beliebigen SharePoint-Projekt hinzu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f95533a5ad3955ee00829194bc4da1498baace0
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850675"
---
# <a name="how-to-create-a-bdc-model"></a>Vorgehensweise: Erstellen eines BDC-Modells
  Sie können ein BDC (Business Data Connectivity)-Modell erstellen, indem Sie die Vorlage für diesen Vorlagentyp verwenden und dann das Modell zu einem SharePoint-Projekt hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md). Weitere Informationen zum Entwerfen des Modells finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>So erstellen Sie ein BDC-Projekt

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

    > [!NOTE]
    > Wenn die IDE für die Verwendung Visual Basic Entwicklungseinstellungen festgelegt ist, wählen Sie **Datei**  >  **neu Projekt** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Wählen Sie unter **Visual Basic** oder **Visual c#** die Option **Office/SharePoint**, **SharePoint-Lösungen** aus.

3. Wählen Sie im Bereich **Vorlagen** das **Projekt Element SharePoint 2013-Empty** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird geöffnet.

4. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL einer SharePoint-Website auf dem lokalen Computer an, wählen Sie das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     Sie werden das Modell auf der von Ihnen angegebenen SharePoint-Website testen.

    > [!IMPORTANT]
    > Sie müssen das Projekt als Farmlösung bereitstellen, da BDC-Modelle ausschließlich Farmlösungen unterstützen.

     Ein leeres SharePoint-Projekt wurde erstellt.

5. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

6. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Office/SharePoint** aus.

7. Wählen Sie in der Liste der SharePoint-Vorlagen die **Option Business Data Connectivity-Modell (nur Farm Lösung)** aus.

8. Geben Sie im Feld **Name** einen Namen für das BDC-Modell an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Dem Projekt wird ein **Business Data Connectivity-Modell** Element hinzugefügt. Standardmäßig wird das Modell im BDC-Designer angezeigt. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Siehe auch
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [How to: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [How to: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
