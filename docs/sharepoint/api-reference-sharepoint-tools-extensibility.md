---
title: API-Referenz (Erweiterbarkeit von SharePoint-Tools) | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62987986"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>API-Referenz (Erweiterbarkeit von SharePoint-Tools)
  Dieser Abschnitt enthält die API-Referenzdokumentation zum Erweitern der SharePoint-Tools in Visual Studio.

## <a name="in-this-section"></a>In diesem Abschnitt
 <xref:Microsoft.VisualStudio.SharePoint>

 Enthält Typen, mit denen Sie das SharePoint-Projektsystem erweitern können. Sie können z. B. die integrierten SharePoint-Projekte und -Projektelemente erweitern, oder Sie können eigene Projektelemente erstellen.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Enthält Typen, die Sie zum Erstellen von benutzerdefinierten *SharePoint-Befehlen*verwenden können. Ein SharePoint-Befehl ist eine Methode, die einen Aufruf in das SharePoint-Serverobjektmodell von einer SharePoint-Tools-Erweiterung aus durchführt.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Enthält Typen, mit denen Sie den Bereitstellungsprozess für SharePoint-Projekte erweitern können.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Enthält Typen, die Sie zum Erweitern von SharePoint-Knoten in **Server-Explorer** oder zum Definieren eigener Knoten Typen verwenden.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Enthält Typen, die Sie verwenden können, um Informationen über integrierte **Server-Explorer** Knoten zu erhalten, die einzelne Komponenten auf einer SharePoint-Website darstellen, z. b. einen Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Enthält Typen, mit denen Sie in einem SharePoint-Projekt auf die Definition einer Funktion zugreifen können.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Enthält Typen, mit denen Sie in einem SharePoint-Projekt auf die Paketdefinition zugreifen können.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Enthält Typen, mit denen Apps zur Kommunikation mit SharePoint authentifiziert werden können, die auf Remote-SharePoint-Websites bereitgestellt werden.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Enthält Typen, mit denen Sie SharePoint-Remotebefehle für SharePoint-Apps erstellen können, die auf SharePoint-Websites bereitgestellt werden.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Enthält Typen, die von Visual Studio als Buildaufgaben für das Verpacken und Debuggen von SharePoint-Projekten, Apps für Office und Apps für SharePoint verwendet werden. Diese API unterstützt die Office- und SharePoint-Infrastruktur und ist nicht für eine direkte Verwendung vom Code aus vorgesehen.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Enthält Typen, mit denen Sie für ein SharePoint-Projekt das Funktions- und Paketvalidierungsverhalten anpassen können.

## <a name="see-also"></a>Weitere Informationen
- [Referenz &#40;Erweiterbarkeit von SharePoint-Tools&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des Knotens "SharePoint-Verbindungen" in Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
