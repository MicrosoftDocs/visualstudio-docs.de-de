---
title: Erweitern des SharePoint-Verbindungs Knotens in Server-Explorer | Microsoft-Dokumentation
titleSuffix: ''
description: Erweitern Sie den Knoten SharePoint-Verbindungen im Fenster Server-Explorer in Visual Studio. Hinzufügen von benutzerdefinierten Eigenschaften zu Knoten. Daten für integrierte Knoten erhalten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56b635db6a8b0c24e2604940fe7500bb8f769a1b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672560"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer
  In Visual Studio können Sie eine Verbindung mit lokalen SharePoint-Sites auf dem Entwicklungs Computer herstellen, indem Sie im **Server-Explorer** Fenster den Knoten **SharePoint-Verbindungen** verwenden. Dieser Knoten zeigt viele der Komponenten von lokalen SharePoint-Sites in einer hierarchischen Strukturansicht an. Beispielsweise können Sie die Listen, Dokument Bibliotheken und Inhaltstypen auf lokalen Websites anzeigen. Weitere Informationen zum Verwenden von **Server-Explorer** zum Herstellen einer Verbindung mit lokalen SharePoint-Websites finden Sie unter [Durchsuchen von SharePoint-Verbindungen mithilfe Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Sie können den Knoten **SharePoint-Verbindungen** erweitern, indem Sie Erweiterungen für vorhandene Knoten erstellen, oder indem Sie einen benutzerdefinierten Knotentyp erstellen und ihn der Knoten Hierarchie hinzufügen.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Aufgaben zum Erweitern des SharePoint-Verbindungs Knotens
 Um einen vorhandenen Knoten zu erweitern, erstellen Sie eine Visual Studio-Erweiterung, die die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle implementiert. Wenn Sie einen Knoten erweitern, können Sie dem Knoten Funktionen hinzufügen, z. b. eigene Kontextmenü Elemente oder benutzerdefinierte Eigenschaften. Weitere Informationen finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Erstellen Sie zum Erstellen eines benutzerdefinierten Knoten Typs eine Visual Studio-Erweiterung, die die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle implementiert. Erstellen Sie einen benutzerdefinierten Knoten, wenn Sie Komponenten von SharePoint-Websites anzeigen möchten, die nicht standardmäßig in **Server-Explorer** angezeigt werden. Beispielsweise zeigt **Server-Explorer** nicht standardmäßig den Webpartkatalog einer SharePoint-Website an, Sie können jedoch einen benutzerdefinierten Knoten hinzufügen, der dies bewirkt. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) und Exemplarische Vorgehensweise [: erweitern Server-Explorer, um Webparts anzuzeigen](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Hinzufügen von benutzerdefinierten Eigenschaften zu Knoten
 Wenn Sie einen Knoten erweitern oder einen benutzerdefinierten Knotentyp erstellen, können Sie dem Knoten benutzerdefinierte Eigenschaften hinzufügen. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt, wenn der Knoten ausgewählt wird.

 Es gibt zwei Arten von benutzerdefinierten Eigenschaften, die Sie einem Knoten hinzufügen können:

- Eigenschaften, die einen Satz Schreib geschützter Daten von der SharePoint-Website anzeigen. Die Daten beschreiben die SharePoint-Komponente, die der Knoten darstellt. Eine exemplarische Vorgehensweise, die die Vorgehensweise veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Eigenschaften, die benutzerdefinierte Lese-/Schreibdaten anzeigen. Ein Codebeispiel, in dem veranschaulicht wird, wie Sie dies tun, finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Daten für integrierte Knoten erhalten
 Alle von Visual Studio bereitgestellten integrierten Knoten enthalten einige Daten über die SharePoint-Komponente, die Sie darstellen. Beispielsweise werden von einem Knoten, der eine Liste auf der SharePoint-Website darstellt, einige Daten zur Liste bereitstellt, z. b. der Titel und die URL der Standardansicht für die Liste.

 Um auf diese Daten zuzugreifen, rufen Sie ein Datenobjekt aus der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des-Objekts ab, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> das den für Sie interessanten Knoten darstellt. Der Typ des Datenobjekts hängt vom Typ des Knotens ab.

 Im folgenden Codebeispiel wird veranschaulicht, wie Sie das Datenobjekt für einen Listen Knoten erhalten. Um dieses Beispiel im Kontext eines größeren Beispiels anzuzeigen, finden Sie unter Gewusst [wie: Anzeigen von Daten für einen integrierten SharePoint-Knoten in Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 In der folgenden Tabelle werden die Datenobjekt Typen für jeden integrierten Knotentyp aufgelistet.

|Knotentyp|Daten Objekttyp|
|---------------|----------------------|
|SharePoint-Website Knoten|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Inhaltstyp|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Funktion|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Feld|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Listen Vorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Listenansicht (Microsoft. SharePoint. spview)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Workflow Zuordnung|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Workflow Vorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Weitere Informationen zur Verwendung der- <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Vorgehensweise: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Gewusst wie: erhalten von Daten für einen integrierten SharePoint-Knoten in Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
