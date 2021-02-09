---
title: 'Vorgehensweise: Erstellen eines SharePoint-Befehls | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie einen benutzerdefinierten SharePoint-Befehl erstellen, um die API des Server Objektmodells in einer SharePoint-Tools-Erweiterung aufzurufen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 51b80124f7cf550843ad346e9d1e1c0b21ccd0f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923351"
---
# <a name="how-to-create-a-sharepoint-command"></a>Vorgehensweise: Erstellen eines SharePoint-Befehls
  Wenn Sie das Server Objektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint-Befehl* erstellen, um die API aufzurufen. Sie definieren den SharePoint-Befehl in einer Assembly, die das Server Objektmodell direkt abrufen kann.

 Weitere Informationen zum Zweck von SharePoint-Befehlen finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

### <a name="to-create-a-sharepoint-command"></a>So erstellen Sie einen SharePoint-Befehl

1. Erstellen Sie ein Klassen Bibliotheksprojekt mit der folgenden Konfiguration:

    - Zielt auf den .NET Framework 3,5 ab. Weitere Informationen zum Auswählen des Ziel-Frameworks finden [Sie unter Gewusst wie: Ausrichten auf eine Version der .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Zielt auf die anycpu-oder x64-Plattform ab. Standardmäßig ist die Zielplattform für Klassen Bibliotheks Projekte anycpu. Weitere Informationen zum Auswählen der Zielplattform finden Sie unter Gewusst [wie: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Ein SharePoint-Befehl kann nicht im selben Projekt implementiert werden, das eine Erweiterung der SharePoint-Tools definiert, da SharePoint-Befehle auf das .NET Framework 3,5-und SharePoint-Tools-Erweiterungen abzielen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Sie müssen alle SharePoint-Befehle definieren, die von der Erweiterung in einem separaten Projekt verwendet werden. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. Erstellen Sie in einer Klasse im Projekt eine Methode, die den SharePoint-Befehl definiert. Die-Methode muss den folgenden Richtlinien entsprechen:

    - Sie kann über einen oder zwei Parameter verfügen.

         Der erste Parameter muss ein- <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Objekt sein. Dieses Objekt stellt das Microsoft. SharePoint. SPSite-oder Microsoft. SharePoint. SPWeb-Objekt bereit, in dem der Befehl ausgeführt wird. Außerdem wird ein Objekt bereitgestellt <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> , das zum Schreiben von Nachrichten in das **Ausgabe** Fenster oder **Fehlerliste** Fenster in Visual Studio verwendet werden kann.

         Der zweite Parameter kann ein Typ Ihrer Wahl sein, aber dieser Parameter ist optional. Sie können diesen Parameter zum SharePoint-Befehl hinzufügen, wenn Sie Daten aus der Erweiterung der SharePoint-Tools an den Befehl übergeben müssen.

    - Sie kann einen Rückgabewert haben, aber dies ist optional.

    - Der zweite Parameter und der Rückgabewert müssen ein Typ sein, der vom Windows Communication Foundation (WCF) serialisiert werden kann. Weitere Informationen finden Sie [unter vom Datenvertragsserialisierer unterstützte Typen](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) und [Verwenden der XmlSerializer-Klasse](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Die-Methode kann über eine beliebige Sichtbarkeit (**öffentlich**, **intern** oder **Privat**) verfügen, und Sie kann statisch oder nicht statisch sein.

4. Wenden <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> Sie das auf die-Methode an. Dieses Attribut gibt einen eindeutigen Bezeichner für den Befehl an. Dieser Bezeichner muss nicht mit dem Methodennamen identisch sein.

     Sie müssen denselben eindeutigen Bezeichner angeben, wenn Sie den Befehl von der SharePoint-Tools-Erweiterung aus aufgerufen haben. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird ein SharePoint-Befehl veranschaulicht, der über den-Bezeichner verfügt `Contoso.Commands.UpgradeSolution` . Dieser Befehl verwendet APIs im Server-Objektmodell, um ein Upgrade auf eine bereitgestellte Lösung auszuführen.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Zusätzlich zum impliziten ersten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter verfügt dieser Befehl auch über einen benutzerdefinierten Zeichen folgen Parameter, der den vollständigen Pfad der wsp-Datei enthält, die auf die SharePoint-Website aktualisiert wird. Um diesen Code im Kontext eines größeren Beispiels anzuzeigen, finden Sie weitere Informationen unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Bereitstellen des Befehls
 Zum Bereitstellen des Befehls fügen Sie die befehlsassembly in das gleiche [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (*VSIX*) mit der Erweiterungsassembly ein, die den Befehl verwendet. Außerdem müssen Sie in der Datei Extension. vsixmanifest einen Eintrag für die befehlsassembly hinzufügen. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Vorgehensweise: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
