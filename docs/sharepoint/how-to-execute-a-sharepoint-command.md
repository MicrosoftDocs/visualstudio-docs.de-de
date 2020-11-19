---
title: 'Vorgehensweise: Ausführen eines SharePoint-Befehls | Microsoft-Dokumentation'
description: Weitere Informationen finden Sie unter Erstellen eines benutzerdefinierten SharePoint-Befehls zum Abrufen der Server Objektmodell-API aus einer SharePoint-Tools-Erweiterung.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2746704e30a61b0971db50a5083855b4a93560d4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903534"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Vorgehensweise: Ausführen eines SharePoint-Befehls
  Wenn Sie das Server Objektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint-Befehl* erstellen, um die API aufzurufen. Nachdem Sie den Befehl definiert und mit der Erweiterung der SharePoint-Tools bereitgestellt haben, kann die Erweiterung den Befehl ausführen, um das SharePoint-Server Objektmodell aufzurufen. Verwenden Sie zum Ausführen des Befehls eine der ExecuteCommand-Methoden eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekts.

 Weitere Informationen zum Zweck von SharePoint-Befehlen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

### <a name="to-execute-a-sharepoint-command"></a>So führen Sie einen SharePoint-Befehl aus

1. In der Erweiterung der SharePoint-Tools können Sie ein- <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt erhalten. Die Art und Weise, wie Sie ein Objekt erhalten, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> hängt vom Typ der Erweiterung ab, die Sie erstellen:

    - In einer Erweiterung des SharePoint-Projekt Systems verwenden Sie die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> Eigenschaft.

         Weitere Informationen zu Projekt Systemerweiterungen finden Sie unter [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md).

    - Verwenden Sie in einer Erweiterung des **SharePoint-Verbindungs** Knotens in **Server-Explorer** die- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> Eigenschaft. Verwenden Sie die-Eigenschaft, um ein-Objekt zu erhalten <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> .

         Weitere Informationen zu **Server-Explorer** Erweiterungen finden Sie unter [Erweitern des SharePoint-Verbindungs Knotens in Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Verwenden Sie in Code, der nicht Teil einer Erweiterung der SharePoint-Tools ist, wie z. b. ein Projektvorlagen-Assistent, die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Eigenschaft.

         Weitere Informationen zum Abrufen des Project Service finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

2. Ruft eine der ExecuteCommand-Methoden des- <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekts auf. Übergeben Sie den Namen des auszuführenden Befehls an das erste Argument der ExecuteCommand-Methode. Wenn der Befehl über einen benutzerdefinierten Parameter verfügt, übergeben Sie diesen Parameter an das zweite Argument der ExecuteCommand-Methode.

     Für jede unterstützte Befehls Signatur gibt es eine andere ExecuteCommand-Überladung. In der folgenden Tabelle sind die unterstützten Signaturen und die für jede Signatur zu verwendende Überladung aufgeführt.

    |Befehls Signatur|Zu verwendende ExecuteCommand-Überladung|
    |-----------------------|------------------------------------|
    |Der Befehl weist nur den Standard <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und keinen Rückgabewert auf.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl hat nur den Standard <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl verfügt über zwei Parameter (den Standard <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und einen benutzerdefinierten Parameter) und keinen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl verfügt über zwei Parameter und einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie die-Überladung verwendet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> wird, um den Befehl aufzurufen `Contoso.Commands.UpgradeSolution` , der in Gewusst [wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)beschrieben wird.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 Die `Execute` in diesem Beispiel gezeigte-Methode ist eine Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> Methode der- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> Schnittstelle in einem benutzerdefinierten Bereitstellungs Schritt. Um diesen Code im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Beachten Sie die folgenden Details zum-Methoden aufzurufen <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> :

- Der erste Parameter identifiziert den Befehl, den Sie aufrufen möchten. Diese Zeichenfolge entspricht dem Wert, den Sie in <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> der Befehls Definition an übergeben.

- Der zweite Parameter ist der Wert, den Sie an den benutzerdefinierten zweiten Parameter des Befehls übergeben möchten. In diesem Fall handelt es sich um den vollständigen Pfad der *wsp* -Datei, die auf die SharePoint-Website aktualisiert wird.

- Der Code übergibt nicht den impliziten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter an den Befehl. Dieser Parameter wird automatisch an den Befehl übergeben, wenn Sie den Befehl aus einer Erweiterung des SharePoint-Projekt Systems oder einer Erweiterung des **SharePoint-Verbindungs** Knotens in **Server-Explorer** aufrufen. In anderen Arten von Projektmappen, wie z. b. in einem Projektvorlagen-Assistenten, der die- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle implementiert, ist dieser Parameter **null**.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert einen Verweis auf die Microsoft. VisualStudio. SharePoint-Assembly.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
