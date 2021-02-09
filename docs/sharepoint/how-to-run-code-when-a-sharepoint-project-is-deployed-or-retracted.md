---
title: Ausführen von Code, wenn das SharePoint-Projekt bereitgestellt oder zurückgezogen wird
titleSuffix: ''
description: Erfahren Sie, wie Sie Code ausführen, wenn ein SharePoint-Projekt bereitgestellt oder zurückgezogen wird, damit Sie Ereignisse behandeln können, die von Visual Studio ausgelöst werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3362606a7e8c5f2278c2ebfb973321e5b8f3157e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850138"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Gewusst wie: Ausführen von Code beim Bereitstellen oder zurückziehen eines SharePoint-Projekts
  Wenn Sie zusätzliche Aufgaben ausführen möchten, wenn ein SharePoint-Projekt bereitgestellt oder zurückgezogen wird, können Sie Ereignisse behandeln, die von Visual Studio ausgelöst werden. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>So führen Sie Code aus, wenn ein SharePoint-Projekt bereitgestellt oder zurückgezogen wird

1. Erstellen Sie eine Projekt Element Erweiterung, eine Projekt Erweiterung oder eine Definition eines neuen Projekt Elementtyps. Weitere Informationen finden Sie unter den folgenden Themen:

   - [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Greifen Sie in der-Erweiterung auf das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt zu. Weitere Informationen finden Sie unter Gewusst [wie: Abrufen des SharePoint-Projekt Dienstanbieter](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Behandeln Sie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> -Ereignis und das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignis des Project Service.

4. Verwenden Sie in den Ereignis Handlern den- <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> Parameter, um Informationen über die aktuelle Bereitstellungs Sitzung zu erhalten. Beispielsweise können Sie bestimmen, welches Projekt in der aktuellen Bereitstellungs Sitzung und ob es bereitgestellt oder zurückgezogen wird.

   Im folgenden Codebeispiel wird veranschaulicht, wie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> -Ereignis und das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignis in einer Projekt Erweiterung behandelt werden. Diese Erweiterung schreibt eine zusätzliche Nachricht in das **Ausgabe** Fenster, wenn die Bereitstellung für ein SharePoint-Projekt gestartet und abgeschlossen wird.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
