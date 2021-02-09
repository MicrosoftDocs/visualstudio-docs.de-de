---
title: 'Vorgehensweise: Behandeln von Bereitstellungs Konflikten | Microsoft-Dokumentation'
description: Sehen Sie sich ein Beispiel für das Implementieren von eigenem Code zum Behandeln von Bereitstellungs Konflikten für ein SharePoint-Projekt Element an.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c163aa10bdcb3ee28de6d6950dd15f85df876bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885611"
---
# <a name="how-to-handle-deployment-conflicts"></a>Vorgehensweise: Behandeln von Bereitstellungs Konflikten
  Sie können eigenen Code bereitstellen, um Bereitstellungs Konflikte für ein SharePoint-Projekt Element zu behandeln. Beispielsweise können Sie feststellen, ob Dateien im aktuellen Projekt Element bereits am Bereitstellungs Speicherort vorhanden sind, und dann die bereitgestellten Dateien löschen, bevor das aktuelle Projekt Element bereitgestellt wird. Weitere Informationen zu Bereitstellungs Konflikten finden Sie unter [Erweitern der SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>So behandeln Sie einen Bereitstellungs Konflikt

1. Erstellen Sie eine Projekt Element Erweiterung, eine Projekt Erweiterung oder eine Definition eines neuen Projekt Elementtyps. Weitere Informationen finden Sie unter den folgenden Themen:

    - [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Behandeln Sie in der-Erweiterung das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Ereignis eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekts (in einer Projekt Element Erweiterung oder Projekt Erweiterung) oder eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekts (in einer Definition eines neuen Projekt Elementtyps).

3. Bestimmen Sie im-Ereignishandler, ob ein Konflikt zwischen dem bereitgestellten Projekt Element und der bereitgestellten Lösung auf der SharePoint-Website vorliegt, basierend auf den Kriterien, die für Ihr Szenario gelten. Mit der- <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> Eigenschaft des Parameters Ereignis Argumente können Sie das Projekt Element analysieren, das bereitgestellt wird, und Sie können die Dateien am Bereitstellungs Speicherort analysieren, indem Sie einen SharePoint-Befehl aufrufen, den Sie zu diesem Zweck definieren.

     Für viele Arten von Konflikten können Sie zuerst bestimmen, welcher Bereitstellungs Schritt ausgeführt wird. Verwenden Sie hierzu die- <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Eigenschaft des Parameters Ereignis Argumente. Obwohl es in der Regel sinnvoll ist, Konflikte während der integrierten <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> Bereitstellung zu erkennen, können Sie während eines beliebigen Bereitstellungs Schritts auf Konflikte überprüfen.

4. Wenn ein Konflikt vorliegt, verwenden Sie die- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> Methode der- <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Eigenschaft der Ereignis Argumente, um ein neues-Objekt zu erstellen <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> . Dieses Objekt stellt den Bereitstellungs Konflikt dar. Geben Sie in Ihrem Aufruf der- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> Methode auch die Methode an, die aufgerufen wird, um den Konflikt aufzulösen.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird der grundlegende Prozess für die Behandlung eines Bereitstellungs Konflikts in einer Projekt Element Erweiterung für Listen Definitions Projekt Elemente veranschaulicht. Um einen Bereitstellungs Konflikt für einen anderen Projekttyp zu behandeln, übergeben Sie eine andere Zeichenfolge an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md).

 Der Einfachheit halber <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> geht der Ereignishandler in diesem Beispiel davon aus, dass ein Bereitstellungs Konflikt vorliegt (d. h., er fügt immer ein neues- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt hinzu), und die- `Resolve` Methode gibt einfach **true** zurück, um anzugeben, dass der Konflikt gelöst wurde. In einem realen Szenario ermittelt der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Ereignishandler zunächst, ob zwischen einer Datei im aktuellen Projekt Element und einer Datei am Bereitstellungsort ein Konflikt besteht, und fügt dann ein Objekt nur dann hinzu, <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Wenn ein Konflikt vorliegt. Beispielsweise können Sie die- `e.ProjectItem.Files` Eigenschaft im-Ereignishandler verwenden, um die Dateien im Projekt Element zu analysieren, und Sie können einen SharePoint-Befehl zum Analysieren der Dateien am Bereitstellungsort abrufen. Ebenso kann die Methode in einem realen Szenario `Resolve` einen SharePoint-Befehl zum Auflösen des Konflikts auf der SharePoint-Website aufzurufen. Weitere Informationen zum Erstellen von SharePoint-Befehlen finden [Sie unter Gewusst wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungs Schritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)
