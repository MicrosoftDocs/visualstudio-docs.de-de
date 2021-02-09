---
title: Aufrufen der SharePoint-Objekt Modelle | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die beiden unterschiedlichen Objekt Modelle aufzurufen, die Sie in Erweiterungen für SharePoint-Tools verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928938"
---
# <a name="call-into-the-sharepoint-object-models"></a>Aufrufe in die SharePoint-Objekt Modelle
  Wenn Sie Erweiterungen für die SharePoint-Tools in Visual Studio erstellen, müssen Sie möglicherweise SharePoint-APIs zum Ausführen bestimmter Aufgaben abrufen. Wenn Sie z. b. einen benutzerdefinierten Bereitstellungs Schritt für SharePoint-Projekte erstellen, müssen Sie möglicherweise SharePoint-APIs aufzurufen, um einige der Aufgaben zum Bereitstellen von Lösungen auszuführen.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] stellen zwei unterschiedliche Objekt Modelle bereit, die Sie in Erweiterungen für SharePoint-Tools verwenden können: ein Server Objektmodell und ein Client Objektmodell. Jedes Objektmodell hat vor-und Nachteile im Zusammenhang mit SharePoint-Tools-Erweiterungen.

 Eine Übersicht über die SharePoint-Objekt Modelle finden Sie unter [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Verwenden des Client Objektmodells in Erweiterungs Projekten
 Wenn Sie eine Erweiterung für die SharePoint-Tools entwickeln, können Sie das Client Objektmodell in Ihrem Projekt wie alle anderen verwalteten APIs verwenden. Sie können dem Projekt Verweise auf Assemblys im Client Objektmodell hinzufügen, und Sie können APIs im Client Objektmodell direkt aus dem Code abrufen.

 Das Client Objektmodell hat jedoch im Kontext der Erweiterungen für SharePoint-Tools zwei Nachteile:

- Das Client Objektmodell stellt nur eine Teilmenge des Server Objektmodells bereit. Wenn Sie SharePoint-Funktionen verwenden müssen, die nicht im Client Objektmodell verfügbar gemacht werden, müssen Sie das Server-Objektmodell verwenden.

- Obwohl die Verwendung des Client Objektmodells in Erweiterungen von SharePoint-Tools in den meisten Fällen funktionieren sollte, können einige Szenarios auftreten, in denen Aufrufe des Client Objektmodells nicht erwartungsgemäß funktionieren. Das Client Objektmodell ist für die Verwendung in Client Anwendungen zum Abrufen von SharePoint-Websites auf einem Remote Server oder einer Remote Farm konzipiert. Die SharePoint-Tools in Visual Studio funktionieren nur mit einer lokalen SharePoint-Installation auf dem Entwicklungs Computer. Wenn Sie das Client Objektmodell in einer SharePoint-Tools-Erweiterung verwenden, wird daher eine SharePoint-Website auf dem lokalen Computer aufgerufen, sodass das Client Objektmodell nicht für die Verwendung vorgesehen ist.

  Eine exemplarische Vorgehensweise, die veranschaulicht, wie das Client Objektmodell in einer Erweiterung der SharePoint-Tools in Visual Studio verwendet wird, finden Sie unter Exemplarische Vorgehensweise [: Abrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Verwenden des Server Objektmodells in Erweiterungs Projekten
 Das Server Objektmodell ist eine übergeordnete Gruppe des Client Objektmodells. Wenn Sie das Server-Objektmodell verwenden, können Sie alle Features verwenden, die und Programm gesteuert verfügbar machen [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .

 Erweiterungen für SharePoint-Tools können APIs im Server-Objektmodell verwenden, aber Sie können die APIs nicht direkt aufzurufen. Das Server Objektmodell kann nur von einem 64-Bit-Prozess aufgerufen werden, der auf den .NET Framework 3,5 abzielt. Für SharePoint-Tools-Erweiterungen ist jedoch erforderlich, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und Sie werden im 32-Bit-Visual Studio-Prozess ausgeführt. Dadurch wird verhindert, dass SharePoint-Tool Erweiterungen direkt auf die Assemblys im SharePoint-Server Objektmodell verweisen.

 Wenn Sie das Server Objektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint-Befehl* erstellen, um die API aufzurufen. Sie definieren den SharePoint-Befehl in einer sekundären Assembly, die das Server Objektmodell direkt aufzurufen. In Ihrem Erweiterungsprojekt können Sie den SharePoint-Befehl indirekt aufrufen, indem Sie die ExecuteCommand-Methode eines- <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekts verwenden.

 Weitere Informationen zum Erstellen und Verwenden von SharePoint-Befehlen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md) und Gewusst [wie: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md). Weitere Informationen zum Bereitstellen von SharePoint-Befehlen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Exemplarische Vorgehensweisen zum Erstellen und Verwenden von SharePoint-Befehlen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) und Exemplarische Vorgehensweise [: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Grundlegendes zur Ausführung von SharePoint-Befehlen
 Assemblys, die SharePoint-Befehle definieren, werden in einen 64-Bit-Host Prozess namens *vssphost4.exe* geladen. Nachdem Sie einen SharePoint-Befehl in einer SharePoint-Tools-Erweiterung aufgerufen haben, wird der Befehl von *vssphost4.exe* anstelle des 32-Bit-Visual Studio-Prozesses (*devenv.exe*) ausgeführt. Sie können einige Aspekte der Ausführung von SharePoint-Befehlen steuern, indem Sie Werte in der Registrierung festlegen. Weitere Informationen finden Sie unter [Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Vorgehensweise: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
