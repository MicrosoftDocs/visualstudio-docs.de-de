---
title: 'Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie einen benutzerdefinierten SharePoint-Knoten zu Server-Explorer in Visual Studio hinzu. Zeigen Sie zusätzliche SharePoint-Komponenten an, die standardmäßig nicht in Server-Explorer angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbee6d780c7f447c8b47f7b478531cb58cef94fd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915465"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer
  Sie können benutzerdefinierte Knoten unter dem Knoten **SharePoint-Verbindungen** in **Server-Explorer** hinzufügen. Dies ist hilfreich, wenn Sie zusätzliche SharePoint-Komponenten anzeigen möchten, die nicht standardmäßig in **Server-Explorer** angezeigt werden. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Um einen benutzerdefinierten Knoten hinzuzufügen, erstellen Sie zuerst eine Klasse, die den neuen Knoten definiert. Erstellen Sie dann eine Erweiterung, mit der der Knoten einem vorhandenen Knoten als untergeordnetes Element hinzugefügt wird.

### <a name="to-define-the-new-node"></a>So definieren Sie den neuen Knoten

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>-Schnittstelle implementiert.

4. Fügen Sie der-Klasse die folgenden Attribute hinzu:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Sie den Typ an den Attributkonstruktor.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. In einer Knoten Definition gibt dieses Attribut den Zeichen folgen Bezeichner für den neuen Knoten an. Es wird empfohlen, dass Sie das Format *Firmenname* verwenden. *Knoten Name* , um sicherzustellen, dass alle Knoten über einen eindeutigen Bezeichner verfügen.

5. Verwenden Sie in ihrer Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> Methode Member des *typeDefinition* -Parameters, um das Verhalten des neuen Knotens zu konfigurieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> Objekt, das den Zugriff auf die in der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle definierten Ereignisse ermöglicht.

     Im folgenden Codebeispiel wird veranschaulicht, wie ein neuer Knoten definiert wird. In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>So fügen Sie den neuen Knoten als untergeordnetes Element eines vorhandenen Knotens hinzu

1. Erstellen Sie im gleichen Projekt wie die Knoten Definition eine Klasse, die die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle implementiert.

2. Fügen Sie der Klasse das <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut hinzu. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Sie den Typ an den Attributkonstruktor.

3. Fügen Sie der Klasse das <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut hinzu. In einer Knoten Erweiterung gibt dieses Attribut den Zeichen folgen Bezeichner für den Typ des Knotens an, den Sie erweitern möchten.

     Zum angeben integrierter Knoten Typen, die von Visual Studio bereitgestellt werden, übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Verwenden Sie diese Werte, um Standort Verbindungsknoten (die Knoten, auf denen Site-URLs angezeigt werden), Standort Knoten oder alle anderen übergeordneten Knoten in **Server-Explorer** anzugeben.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die eine einzelne Komponente auf einer SharePoint-Website darstellen, z. b. einen Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.

4. <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Ereignis des-Parameters in der Implementierung der-Methode <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> .

5. Fügen Sie im-Ereignishandler der Auflistung untergeordneter <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Knoten des- <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> Objekts, das durch den Parameter Ereignis Argumente verfügbar gemacht wird, den neuen Knoten hinzu.

     Im folgenden Codebeispiel wird veranschaulicht, wie der neue Knoten dem Knoten SharePoint-Website in **Server-Explorer** als untergeordnetes Element hinzugefügt wird.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Vollständiges Beispiel
 Im folgenden Codebeispiel wird der gesamte Code bereitgestellt, um einen einfachen Knoten zu definieren und ihn als untergeordnetes Element des SharePoint-Website Knotens in **Server-Explorer** hinzuzufügen.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Kompilieren des Codes
 In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält. Dieses Beispiel erfordert auch Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der **Server-Explorer** Erweiterung ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Vorgehensweise: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
