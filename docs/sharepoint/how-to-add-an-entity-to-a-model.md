---
title: 'Vorgehensweise: Hinzufügen einer Entität zu einem Modell | Microsoft-Dokumentation'
description: Fügen Sie einem Modell eine Entität hinzu, indem Sie ein Entitäts Steuerelement aus der Visual Studio-Toolbox in den Business Data Connectivity (BDC)-Designer einfügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0efd7a6fc0d6254dbfd3cbda538ffe0e30585453
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915387"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Gewusst wie: Hinzufügen einer Entität zu einem Modell
  Um eine Entität zu erstellen, fügen Sie ein Entitäts Steuerelement aus der Visual Studio- **Toolbox** auf dem Business Data Connectivity (BDC)-Designer hinzu.

### <a name="to-add-an-entity-to-the-model"></a>So fügen Sie dem Modell eine Entität hinzu

1. Erstellen Sie ein BDC-Projekt, oder öffnen Sie ein vorhandenes BDC-Projekt. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

2. Fügen Sie in der **Toolbox** aus der Gruppe **BusinessDataCatalog** ein **Entitäts** Steuerelement zum Designer hinzu.

     Die neue Entität wird im Designer angezeigt. Visual Studio fügt dem XML-Code der `<Entity>` BDC-Modelldatei in Ihrem Projekt ein Element hinzu. Weitere Informationen zu den Attributen eines Entity-Elements finden Sie unter [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. Öffnen Sie im Designer das Kontextmenü für die Entität, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Bezeichner** aus.

     In der Entität wird ein neuer Bezeichner angezeigt.

    > [!NOTE]
    > Sie können den Namen der Entität und des Bezeichners im **Eigenschaften** Fenster ändern.

4. Definieren Sie die Felder der Entität in einer Klasse. Sie können dem Projekt entweder eine neue Klasse hinzufügen oder eine vorhandene Klasse verwenden, die mit anderen Tools wie dem objektrelationaler Designer (O/R-Designer) erstellt wurde. Das folgende Beispiel zeigt eine Entitäts Klasse mit dem Namen "Contact".

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
