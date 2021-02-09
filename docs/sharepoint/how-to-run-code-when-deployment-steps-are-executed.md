---
title: 'Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten | Microsoft-Dokumentation'
description: Führen Sie Code aus, um Ereignisse zu behandeln, die von SharePoint-Projekt Elementen vor und nach der Ausführung eines Bereitstellungs Schritts ausgelöst werden.
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
ms.openlocfilehash: 0b3037c0ec983b9f496947feba41938111fafc38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851581"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten
  Wenn Sie zusätzliche Aufgaben für einen Bereitstellungs Schritt in einem SharePoint-Projekt ausführen möchten, können Sie Ereignisse behandeln, die von SharePoint-Projekt Elementen vor und nach der Ausführung der einzelnen Bereitstellungs Schritte ausgelöst werden. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>So führen Sie Code aus, wenn Bereitstellungs Schritte ausgeführt werden

1. Erstellen Sie eine Projekt Element Erweiterung, eine Projekt Erweiterung oder eine Definition eines neuen Projekt Elementtyps. Weitere Informationen finden Sie unter den folgenden Themen:

    - [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Behandeln Sie in der-Erweiterung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignis und das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignis eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekts (in einer Projekt Element Erweiterung oder Projekt Erweiterung) oder eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekts (in einer Definition eines neuen Projekt Elementtyps).

3. Verwenden Sie in den Ereignis Handlern den <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> -Parameter und den- <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> Parameter, um Informationen über den Bereitstellungs Schritt zu erhalten. Beispielsweise können Sie bestimmen, welcher Bereitstellungs Schritt ausgeführt wird und ob die Lösung bereitgestellt oder zurückgezogen wird.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignis und das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignis in einer Erweiterung für das List instance Project-Element behandelt werden. Diese Erweiterung schreibt eine zusätzliche Nachricht in das **Ausgabe** Fenster, wenn Visual Studio den Anwendungs Pool beim Bereitstellen und zurückziehen der Projekt Mappe wieder verwendet.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Gewusst wie: Ausführen von Code beim Bereitstellen oder zurückziehen eines SharePoint-Projekts](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
