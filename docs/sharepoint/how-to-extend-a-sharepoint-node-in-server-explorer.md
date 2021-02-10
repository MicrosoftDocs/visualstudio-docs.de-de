---
title: 'Vorgehensweise: Erweitern eines SharePoint-Knotens in Server-Explorer | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie einen SharePoint-Knoten in Server-Explorer mithilfe des SharePoint-Verbindungs Knotens erweitern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4983930a7c16edef826a5912abf0870598b1f906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943795"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Vorgehensweise: Erweitern eines SharePoint-Knotens in Server-Explorer
  Knoten können unter dem Knoten **SharePoint-Verbindungen** in **Server-Explorer** erweitert werden. Dies ist hilfreich, wenn Sie einem vorhandenen Knoten neue untergeordnete Knoten, Kontextmenü Elemente oder Eigenschaften hinzufügen möchten. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>So erweitern Sie einen SharePoint-Knoten in Server-Explorer

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>-Schnittstelle implementiert.

4. Fügen Sie der Klasse das <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut hinzu. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Sie den Typ an den Attributkonstruktor.

5. Fügen Sie der Klasse das <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut hinzu. Dieses Attribut gibt den Zeichen folgen Bezeichner für den Typ des Knotens an, den Sie erweitern möchten.

     Zum angeben integrierter Knoten Typen, die von Visual Studio bereitgestellt werden, übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Verwenden Sie diese Werte, um Standort Verbindungsknoten (die Knoten, auf denen Site-URLs angezeigt werden), Standort Knoten oder alle anderen übergeordneten Knoten in **Server-Explorer** anzugeben.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die eine einzelne Komponente auf einer SharePoint-Website darstellen, z. b. einen Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.

6. Verwenden Sie in ihrer Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> Methode Member des *NodeType* -Parameters, um dem Knoten Funktionen hinzuzufügen. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> Objekt, das den Zugriff auf die in der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle definierten Ereignisse ermöglicht. Beispielsweise können Sie die folgenden Ereignisse behandeln:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Behandeln Sie dieses Ereignis, um dem Knoten neue untergeordnete Knoten hinzuzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Behandeln Sie dieses Ereignis, um dem Knoten ein benutzerdefiniertes Kontextmenü Element hinzuzufügen.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Behandeln Sie dieses Ereignis, um dem Knoten benutzerdefinierte Eigenschaften hinzuzufügen. Die Eigenschaften werden im **Eigenschaften** Fenster angezeigt, wenn der Knoten ausgewählt wird.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei verschiedene Typen von Knoten Erweiterungen erstellt werden:

- Eine Erweiterung, mit der SharePoint-Website Knoten ein Kontextmenü Element hinzugefügt wird. Wenn Sie auf das Menü Element klicken, wird der Name des Knotens angezeigt, auf den geklickt wurde.

- Eine Erweiterung, mit der jedem Knoten, der ein Feld namens **Body** darstellt, eine benutzerdefinierte Eigenschaft mit dem Namen **condesoexampleproperty** hinzugefügt wird.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Diese Erweiterung fügt Knoten eine editierbare Zeichen folgen Eigenschaft hinzu. Sie können auch benutzerdefinierte Eigenschaften erstellen, die schreibgeschützte Daten vom SharePoint-Server anzeigen. Ein Beispiel, das die Vorgehensweise veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der **Server-Explorer** Erweiterung ein [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
