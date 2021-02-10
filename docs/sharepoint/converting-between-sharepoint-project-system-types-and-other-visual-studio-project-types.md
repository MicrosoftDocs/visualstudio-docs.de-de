---
title: 'Konvertieren: SharePoint-Projekt Systemtypen in/aus anderen Typen'
titleSuffix: ''
description: Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen. Eine Liste mit Details zu den Typen, die konvertiert werden können, finden Sie hier.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc0eca8005c4eee6e1eb89c410b50be5d0228ec6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946331"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konvertieren zwischen SharePoint-Projekt Systemtypen und anderen Visual Studio-Projekttypen
  In einigen Fällen verfügen Sie möglicherweise über ein Objekt im SharePoint-Projekt System, und Sie möchten die Features eines entsprechenden Objekts im Visual Studio-Automatisierungs Objektmodell oder im Integrations Objektmodell verwenden oder umgekehrt. In diesen Fällen können Sie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Methode des SharePoint-Projekt diendiensdienstanbieter verwenden, um das Objekt in ein anderes Objektmodell zu konvertieren.

 Beispielsweise könnten Sie über ein- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt verfügen, aber Sie möchten Methoden verwenden, die nur für ein- <xref:EnvDTE.Project> oder-Objekt verfügbar sind <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . In diesem Fall können Sie die-Methode verwenden, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> um das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in ein <xref:EnvDTE.Project> oder zu konvertieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Weitere Informationen zum Visual Studio-Automatisierungs Objektmodell und zum Visual Studio-Integrations Objektmodell finden Sie unter [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Typen von Konvertierungen
 In der folgenden Tabelle werden die Typen aufgelistet, die diese Methode zwischen dem SharePoint-Projekt System und den anderen Visual Studio-Objekt Modellen konvertieren kann.

|Typ des SharePoint-Projekt Systems|Entsprechende Typen in den Automatisierungs-und Integrations Objekt Modellen|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oder<br /><br /> Eine beliebige Schnittstelle im Visual Studio-Integrations Objektmodell, die vom zugrunde liegenden COM-Objekt für das Projekt implementiert wird. Zu diesen Schnittstellen zählen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (oder eine abgeleitete Schnittstelle) und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Eine Liste der Haupt Schnittstellen, die von-Projekten implementiert werden, finden Sie unter [Projekt Modell-Kernkomponenten](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oder<br /><br /> Ein- <xref:System.UInt32> Wert (auch als vsitemid bezeichnet), der das Projektmitglied in der identifiziert <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , das es enthält. Dieser Wert kann an den *ItemID* -Parameter einiger Methoden übergeben werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Methode zum Konvertieren eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekts in ein-Objekt verwendet wird <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Für dieses Beispiel benötigen Sie Folgendes:

- Eine Erweiterung des SharePoint-Projekt Systems, das einen Verweis auf die *EnvDTE.dll* Assembly enthält. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).

- Code, der die `projectService_ProjectAdded` Methode zum Behandeln des- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> Ereignisses eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekts registriert. Ein Beispiel finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Weitere Informationen

- [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md)
- [Vorgehensweise: Abrufen des SharePoint-Projekt Dienstanbieter](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
