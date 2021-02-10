---
title: Übersicht über benutzerdefinierte Dokumenteigenschaften
description: Wenn Sie ein Projekt auf Dokument Ebene erstellen, werden in Visual Studio dem Dokument im Projekt zwei benutzerdefinierte Eigenschaften hinzugefügt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 51039c71c97614cb9e43df263b3d7155c9cb86f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947800"
---
# <a name="custom-document-properties-overview"></a>Übersicht über benutzerdefinierte Dokumenteigenschaften

Wenn Sie ein Projekt auf Dokument Ebene erstellen, fügt Visual Studio dem Dokument im Projekt zwei benutzerdefinierte Eigenschaften hinzu: \_ assemblylocation und \_ AssemblyName. Wenn ein Benutzer ein Dokument öffnet, überprüft die Microsoft Office-Anwendung, ob diese benutzerdefinierten Dokumenteigenschaften angezeigt werden. Wenn Sie im Dokument vorhanden sind, lädt die Anwendung die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , die die Anpassung startet. Weitere Informationen finden Sie unter [Architektur von Office](../vsto/architecture-of-office-solutions-in-visual-studio.md)-Projektmappen in Visual Studio.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Diese Eigenschaft enthält die CLSID einer Schnittstelle in der Office-projektmappenladeerkomponente von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Der CLSID-Wert ist 4E3C66D5-58d4-491e-A7D4-64AF99AF6E8B. Sie sollten diesen Wert niemals ändern.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Diese Eigenschaft enthält eine Zeichenfolge, die Details zum Bereitstellungs Manifest für die Anpassung bereitstellt. Weitere Informationen zu Manifesten finden Sie unter [Anwendungs-und Bereitstellungs Manifeste in Office-](../vsto/application-and-deployment-manifests-in-office-solutions.md)Projektmappen.

 Der \_ assemblylocation-Eigenschafts Wert kann abhängig von der Bereitstellung der Lösung unterschiedliche Formate aufweisen:

- Wenn die Lösung für die Installation von einer Website, einem UNC-Pfad oder einer CD oder einem USB-Laufwerk veröffentlicht wird, hat die _AssemblyLocation-Eigenschaft das Format *DeploymentManifestPath* | *SolutionId*. Die folgende Zeichenfolge ist ein Beispiel:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Wenn Sie die Projekt Mappe in Visual Studio ausführen oder Debuggen, hat die _AssemblyLocation-Eigenschaft das Format *DeploymentManifestName* | *SolutionId*| vstolocal. Die folgende Zeichenfolge ist ein Beispiel:

     "ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  Die *SolutionId* ist eine GUID, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] von zum Identifizieren der Lösung verwendet wird. Die *SolutionId* wird automatisch generiert, wenn Sie das Projekt erstellen. Der **vstolocal** -Begriff gibt an, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dass die Assembly aus demselben Ordner wie das Dokument geladen werden soll.

## <a name="see-also"></a>Weitere Informationen

- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)
- [Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Gewusst wie: Veröffentlichen einer Office-Projekt Mappe mit ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)