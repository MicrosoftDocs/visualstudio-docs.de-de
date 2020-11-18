---
title: Zuordnen von benutzerdefinierten Daten zu Erweiterungen für SharePoint-Tools | Microsoft-Dokumentation
description: Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools Erweiterungen. Eine Liste der Objekte, die benutzerdefinierte Daten enthalten können, finden Sie hier. Benutzerdefinierte Daten hinzufügen und abrufen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db32c05b4a1f4536e71b4ef233758f747a958327
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850402"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen
  Sie können bestimmten Objekten in Erweiterungen von SharePoint-Tools benutzerdefinierte Daten hinzufügen. Dies ist hilfreich, wenn Sie Daten in einem Teil ihrer Erweiterung haben, auf den Sie später über anderen Code in ihrer Erweiterung zugreifen möchten. Anstatt eine benutzerdefinierte Methode zum Speichern und Zugreifen auf Daten zu implementieren, können Sie die Daten mit einem Objekt in ihrer Erweiterung verknüpfen und die Daten später aus demselben Objekt abrufen.

 Das Hinzufügen von benutzerdefinierten Daten zu Objekten ist auch nützlich, wenn Sie Daten beibehalten möchten, die für ein bestimmtes Element in Visual Studio relevant sind. Erweiterungen für SharePoint-Tools werden nur einmal in Visual Studio geladen, sodass die Erweiterung möglicherweise mit verschiedenen Elementen (z. b. Projekten, Projekt Elementen oder **Server-Explorer** Knoten) zu einem beliebigen Zeitpunkt funktioniert. Wenn Sie über benutzerdefinierte Daten verfügen, die nur für ein bestimmtes Element relevant sind, können Sie die Daten dem-Objekt hinzufügen, das dieses Element darstellt.

 Wenn Sie Objekten in Erweiterungen von SharePoint-Tools benutzerdefinierte Daten hinzufügen, bleiben die Daten nicht erhalten. Die Daten sind nur während der Lebensdauer des-Objekts verfügbar. Nachdem das Objekt von Garbage Collection freigegeben wurde, gehen die Daten verloren.

 In Erweiterungen des SharePoint-Projekt Systems können Sie auch Zeichen folgen Daten speichern, die nach dem Entladen einer Erweiterung beibehalten werden. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Objekte, die benutzerdefinierte Daten enthalten können
 Sie können jedem Objekt im SharePoint-Tools-Objektmodell, das die-Schnittstelle implementiert, benutzerdefinierte Daten hinzufügen <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . Diese Schnittstelle definiert nur eine Eigenschaft, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> , die eine Auflistung von benutzerdefinierten Datenobjekten ist. Die folgenden Typen implementieren <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Hinzufügen und Abrufen von benutzerdefinierten Daten
 Wenn Sie einem Objekt in einer SharePoint-Tools-Erweiterung benutzerdefinierte Daten hinzufügen möchten, können <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Sie die-Eigenschaft des Objekts, dem Sie die Daten hinzufügen möchten, und dann die-Methode verwenden, <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> um die Daten dem-Objekt hinzuzufügen.

 Wenn Sie benutzerdefinierte Daten aus einem Objekt in einer SharePoint-Tools-Erweiterung abrufen möchten, rufen Sie die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft des-Objekts ab, und verwenden Sie dann eine der folgenden Methoden:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Diese Methode gibt **true** zurück, wenn das Datenobjekt vorhanden ist, oder **false** , wenn Sie nicht vorhanden ist. Mit dieser Methode können Sie Instanzen von Werttypen oder Verweis Typen abrufen.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Diese Methode gibt das Datenobjekt zurück, wenn es beendet wird, oder **null** , wenn es nicht vorhanden ist. Diese Methode kann nur zum Abrufen von Instanzen von Verweis Typen verwendet werden.

  Im folgenden Codebeispiel wird bestimmt, ob ein bestimmtes Datenobjekt bereits einem Projekt Element zugeordnet ist. Wenn das Datenobjekt nicht bereits mit dem Projekt Element verknüpft ist, fügt der Code das Objekt der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Projekt Elements hinzu. Um dieses Beispiel im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Gewusst [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Siehe auch
- [Programmierkonzepte und Features für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
