---
title: 'Vorgehensweise: Abrufen des SharePoint-Projekt Dienstanbieter | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie in Projekt Systemerweiterungen, Server-Explorer Erweiterungen oder anderen Visual Studio-Erweiterungen auf den SharePoint-Projekt Dienst zugreifen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 553b4ae3b7ecfa9fa49065824020ebdcecf77215
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304447"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Vorgehensweise: Abrufen des SharePoint-Projekt Dienstanbieter
  Sie können in den folgenden Lösungs Typen auf den SharePoint-Projekt Dienst zugreifen:

- Eine Erweiterung des SharePoint-Projekt Systems, z. b. Projekt Erweiterung, Projekt Element Erweiterung oder Projekt Elementtyp Definition. Weitere Informationen zu diesen Erweiterungs Typen finden Sie unter [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md).

- Eine Erweiterung des **SharePoint-Verbindungs** Knotens in **Server-Explorer**. Weitere Informationen zu diesen Erweiterungs Typen finden Sie unter [Erweitern des SharePoint-Verbindungs Knotens in Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Ein anderer Typ der Visual Studio-Erweiterung, z. b. ein VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Dienst in Projekt Systemerweiterungen abrufen
 In einer beliebigen Erweiterung des SharePoint-Projekt Systems können Sie mithilfe der-Eigenschaft eines Objekts auf den Projekt Dienst zugreifen <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> .

 Sie können den Projekt Dienst auch mithilfe der folgenden Prozeduren abrufen.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>So rufen Sie den Dienst in einer Projekt Erweiterung ab

1. Suchen Sie in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode.

2. Verwenden Sie den *ProjectService* -Parameter, um auf den Dienst zuzugreifen.

     Im folgenden Codebeispiel wird veranschaulicht, wie der Project Service zum Schreiben einer Meldung in das **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Projekt Erweiterung verwendet wird.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Weitere Informationen zum Erstellen von Projekt Erweiterungen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>So rufen Sie den Dienst in einer Projekt Element Erweiterung ab

1. Suchen Sie in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode.

2. Verwenden Sie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> Eigenschaft des *projectItemType* -Parameters, um den Dienst abzurufen.

     Im folgenden Codebeispiel wird veranschaulicht, wie der Project Service zum Schreiben einer Meldung in das **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Erweiterung des Projekt Elements für die **Listen Definition** verwendet wird.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Weitere Informationen zum Erstellen von Projekt Element Erweiterungen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>So rufen Sie den Dienst in einer Projekt Elementtyp Definition ab

1. Suchen Sie in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode.

2. Verwenden Sie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> Eigenschaft des *typeDefinition* -Parameters, um den Dienst abzurufen.

     Im folgenden Codebeispiel wird veranschaulicht, wie der Project Service verwendet wird, um eine Nachricht in das **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Projekt Elementtyp Definition zu schreiben.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Weitere Informationen zum Definieren von Projekt Elementtypen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Abrufen des diensdienstanbieter in Server-Explorer Erweiterungen
 In einer Erweiterung des **SharePoint-Verbindungs** Knotens in **Server-Explorer** können Sie mithilfe der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft eines Objekts auf den Projekt Dienst zugreifen <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>So rufen Sie den Dienst in einer Server-Explorer Erweiterung ab

1. Ein- <xref:System.IServiceProvider> Objekt aus der- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekts in der Erweiterung.

2. Verwenden Sie die- <xref:System.IServiceProvider.GetService%2A> Methode, um ein- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt anzufordern.

     Im folgenden Codebeispiel wird veranschaulicht, wie der Project Service verwendet wird, um eine Nachricht in das **Ausgabe** Fenster zu schreiben, und **Fehlerliste** Fenster in einem Kontextmenü, das von der Erweiterung Listen Knoten in **Server-Explorer** hinzugefügt wird.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Weitere Informationen zum Erweitern des **SharePoint-Verbindungs** Knotens in **Server-Explorer** finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Abrufen des Dienstanbieter in anderen Visual Studio-Erweiterungen
 Sie können den Projekt Dienst in einem VSPackage oder in einer beliebigen Visual Studio-Erweiterung abrufen, die auf ein- <xref:EnvDTE80.DTE2> Objekt im Automation-Objektmodell zugreifen kann, z. b. einen Projektvorlagen-Assistenten, der die- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle implementiert.

 In einem VSPackage können Sie ein Objekt mit <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> einer der folgenden Methoden anfordern:

- Die <xref:System.IServiceProvider.GetService%2A> Methode eines verwalteten VSPackages, das von der- <xref:Microsoft.VisualStudio.Shell.Package> Klasse abgeleitet wird. Weitere Informationen finden Sie unter Gewusst [wie: erhalten eines Dienstanbieter](../extensibility/how-to-get-a-service.md).

- Die statische- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode. Weitere Informationen finden Sie unter [Verwenden von GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  In einer Visual Studio-Erweiterung, die auf ein- <xref:EnvDTE80.DTE2> Objekt zugreifen kann, können Sie ein- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt mit der- <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode eines-Objekts anfordern <xref:Microsoft.VisualStudio.Shell.ServiceProvider> . Weitere Informationen finden Sie unter " [erhalten eines Dienstanbieter" aus dem DTE-Objekt](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Siehe auch
- [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md)
- [Vorgehensweise: erhalten eines Dienstanbieter](../extensibility/how-to-get-a-service.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
