---
title: Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen | Microsoft-Dokumentation
description: Definieren eines benutzerdefinierten SharePoint-Projekt Elementtyps, wenn Sie eine neue Art von SharePoint-Projekt Element erstellen möchten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948868"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen
  Definieren Sie einen neuen SharePoint-Projekt Elementtyp, wenn Sie eine neue Art von SharePoint-Projekt Element erstellen möchten. Beispielsweise enthält Visual Studio keine SharePoint-Projekt Elemente zum Hinzufügen von Feldern oder benutzerdefinierten Aktionen zu einer SharePoint-Website. Sie können eigene Typen von SharePoint-Projekt Elementen definieren, um Felder, benutzerdefinierte Aktionen oder andere Typen von SharePoint-Komponenten zu erstellen.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Aufgaben zum Definieren von SharePoint-Projekt Elementtypen
 Um einen benutzerdefinierten Projekt Elementtyp zu definieren, erstellen Sie eine Visual Studio-Erweiterungsassembly, die die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle implementiert. Weitere Informationen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Wenn Sie einen benutzerdefinierten Projekt Elementtyp definieren, können Sie dem Projekt Element auch die folgenden Funktionen hinzufügen:

- Fügen Sie dem Projekt Element ein Kontextmenü Element hinzu. Das Menü Element wird angezeigt, wenn Sie das Kontextmenü für das Projekt Element in **Projektmappen-Explorer** öffnen, indem Sie mit der rechten Maustaste auf das Projekt Element klicken oder es auswählen und **dann die** + Taste **F10** drücken. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Fügen Sie dem Projekt Element eine benutzerdefinierte Eigenschaft hinzu. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn Sie das Projekt Element in **Projektmappen-Explorer** auswählen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Damit andere Entwickler ihr Projekt Element in Visual Studio verwenden können, erstellen Sie eine spdata-Datei, und erstellen Sie eine Element Vorlage oder Projektvorlage, die dem Projekt Element zugeordnet ist. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Verstehen der Beziehung zwischen Projekt Elementtypen und Projekt Element Instanzen
 Wenn Sie einen SharePoint-Projekt Elementtyp definieren, lädt Visual Studio die Erweiterung, wenn ein Projekt Element des zugeordneten Typs einem SharePoint-Projekt hinzugefügt wird. Wenn Sie z. b. einen neuen Projekt Elementtyp für eine **benutzerdefinierte Aktion** definieren, lädt Visual Studio die Erweiterung, wenn ein Benutzer ein Benutzer **definiertes Aktions** Projekt Element zu einem Projekt hinzufügt. Visual Studio verwendet die gleiche Instanz Ihrer Erweiterung für alle Instanzen des zugeordneten Projekt Elementtyps. Wenn dem Projekt im vorherigen Beispiel ein zweites Benutzer **definiertes Aktions** Projekt Element hinzugefügt wird, wird die gleiche Instanz Ihrer Erweiterung zum Anpassen des zweiten Projekt Elements verwendet.

 Um auf eine bestimmte Instanz des Projekt Elementtyps zuzugreifen, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse des *projectItemTypeDefinition* -Parameters in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Um z. b. zu ermitteln, ob ein Projekt Element des benutzerdefinierten Typs einem Projekt hinzugefügt wird, behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
