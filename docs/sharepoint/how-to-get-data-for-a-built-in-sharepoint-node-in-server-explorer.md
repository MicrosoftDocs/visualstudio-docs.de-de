---
title: Daten für integrierten SharePoint-Knoten in Server-Explorer
titleSuffix: ''
description: Sie erhalten Daten für die zugrunde liegende SharePoint-Komponente eines integrierten SharePoint-Knotens im Server-Explorer Fenster von Visual Studio.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a975374b82b10c0e29d74bcf68d7bce3225a967
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903519"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Gewusst wie: erhalten von Daten für einen integrierten SharePoint-Knoten in Server-Explorer
  Für jeden integrierten SharePoint-Knoten in **Server-Explorer** können Sie Daten für die zugrunde liegende SharePoint-Komponente, die der Knoten darstellt, erhalten. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie Daten für die zugrunde liegende SharePoint-Liste, die ein Listen Knoten in **Server-Explorer** darstellt, erhalten. Standardmäßig haben Listen Knoten eine **Ansicht im** Kontextmenü Element Browser, auf das Sie klicken können, um die Listen in einem Webbrowser zu öffnen. In diesem Beispiel werden Listen Knoten erweitert, indem eine Ansicht im Kontextmenü Element von **Visual Studio** hinzugefügt wird, mit der die Listen direkt in Visual Studio geöffnet werden. Der Code greift auf die Listen Daten für den Knoten zu, um die URL der Liste zu erhalten, die in Visual Studio geöffnet werden soll.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 In diesem Beispiel wird der SharePoint-Projekt Dienst zum Abrufen des- <xref:EnvDTE.DTE> Objekts verwendet, das zum Öffnen von Listen in Visual Studio verwendet wird. Weitere Informationen zum SharePoint-Projekt Dienst finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

 Weitere Informationen zu den grundlegenden Aufgaben zum Erstellen einer Erweiterung für einen SharePoint-Knoten finden Sie unter Gewusst [wie: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der **Server-Explorer** Erweiterung ein [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Vorgehensweise: Erweitern eines SharePoint-Knotens in Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md)
- [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
