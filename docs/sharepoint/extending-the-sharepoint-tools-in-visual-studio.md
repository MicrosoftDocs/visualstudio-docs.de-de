---
title: Erweitern der SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
description: Erweitern der SharePoint-Tools in Visual Studio. Erweitern des SharePoint-Projektsystems. Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c074e62b47b926351948e94d78621a8a41c9c3e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876848"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Erweitern der SharePoint-Tools in Visual Studio
  Die SharePoint-Tools in Visual Studio erfüllen die Anforderungen vieler Anwendungsentwicklungsszenarios. Allerdings treffen Sie möglicherweise auf Fälle, in denen sie keine Funktionen bereitstellen, die Sie oder andere Entwickler benötigen. In diesen Fällen können Sie die SharePoint-Tools erweitern, um die Funktionalität zu erstellen, die Sie benötigen.

## <a name="how-to-extend-the-sharepoint-tools"></a>Vorgehensweise zum Erweitern der SharePoint-Tools
 Sie können das SharePoint-Projektsystem und den Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** erweitern.

### <a name="extend-the-sharepoint-project-system"></a>Erweitern des SharePoint-Projektsystems
 Visual Studio umfasst eine Reihe von Projektvorlagen und Elementvorlagen, die Sie zum Erstellen von SharePoint-Lösungen verwenden können. Beispielsweise stehen Ihnen Vorlagen für Ereignisempfänger, Listendefinitionen, Workflows und Webparts zur Verfügung. Allerdings können Sie auch Ihre eigenen Typen von SharePoint-Projektelementen zum Erstellen von SharePoint-Komponenten definieren, z. B. Felder oder benutzerdefinierte Aktionen. Sie können auch Erweiterungen für SharePoint-Projektelementtypen erstellen, die bereits in Visual Studio installiert sind. Außerdem können Sie Erweiterungen für SharePoint-Projekte erstellen.

 Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer
 In Visual Studio können Sie den Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** verwenden, um viele Komponenten von einer oder mehreren SharePoint-Websites in einer hierarchischen Strukturansicht anzuzeigen. Sie können den Knoten **SharePoint-Verbindungen** auf folgende Weisen erweitern:

- Durch Hinzufügen Ihrer eigenen Knoten: Dieser Ansatz ist nützlich, wenn Sie Komponenten von SharePoint-Websites anzeigen möchten, die nicht standardmäßig angezeigt werden.

- Durch Erweitern vorhandener Knoten: Sie können beispielsweise einen neuen untergeordneten Knoten zu einem vorhandenen Knoten hinzufügen oder ein Kontextmenüelement zu einem Knoten hinzufügen und Aufgaben ausführen, wenn ein Entwickler auf das Menüelement klickt.

  Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Anforderungen an Entwicklungscomputer
 Zum Erstellen von Erweiterungen für die SharePoint-Tools muss Ihr Entwicklungscomputer dieselben Anforderungen erfüllen, die zum Erstellen von SharePoint-Lösungen in Visual Studio bestehen.

 Es wird außerdem empfohlen, dass Sie [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installieren. Das SDK enthält Projektvorlagen und Tools, die Sie zum Erweitern von Visual Studio verwenden können. Insbesondere enthält das SDK eine Projektvorlage, die Sie verwenden können, um mühelos ein VSIX-Paket (Visual Studio-Erweiterungspaket) zu erstellen. VSIX-Pakete sind die bevorzugte Methode zum Bereitstellen von Visual Studio-Erweiterungen in Visual Studio. Alle Erweiterungen für SharePoint-Tools müssen mit VSIX-Paketen bereitgestellt werden. In allen exemplarischen Vorgehensweisen dieser Dokumentation wird vorausgesetzt, dass Sie [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installiert haben.

 Informationen zum Installieren des Visual Studio SDK finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Weitere Informationen über Visual Studio-Erweiterungen finden Sie unter [Einstieg in die Entwicklung von Visual Studio-Erweiterungen](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des Knotens „SharePoint-Verbindungen“ im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programmierkonzepte und Features für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referenz &#40;Erweiterbarkeit von SharePoint-Tools&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)