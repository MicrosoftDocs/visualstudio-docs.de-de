---
title: Vergleich von VBA-und Office-Projektmappen in Visual Studio
description: Erfahren Sie mehr über die Unterschiede zwischen Microsoft Visual Basic for Applications (VBA) und Microsoft Office Lösungen in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a07711fd854bd0dc035cab776f713701d5d85200
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838112"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Vergleich von VBA-und Office-Projektmappen in Visual Studio
  In Microsoft Visual Basic for Applications (VBA) wird nicht verwalteter Code verwendet, der eng in Office-Anwendungen integriert ist. Mit Microsoft Office-Projekten, die mit Visual Studio erstellt wurden, können Sie .NET Framework und Visual Studio-Entwurfstools nutzen.

 Informationen zu den Typen von Office-Projektmappen, die Sie mit Visual Studio erstellen können, finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;v&#41;Sto ](../vsto/office-solutions-development-overview-vsto.md)

## <a name="comparison"></a>Vergleich
 Die folgende Tabelle enthält einen grundlegenden Vergleich von VBA-Projektmappen und Office-Projektmappen in Visual Studio.

|VBA-Projektmappen|Office-Projektmappen in Visual Studio|
|-------------------|---------------------------------------|
|Nutzt Code, der dauerhaft mit einem bestimmten Dokument verbunden ist.|Verwendet Code, der separat vom Dokument (für Anpassungen auf Dokument Ebene) oder in einer Assembly gespeichert ist, die von der Anwendung geladen wird (für VSTO-Add-Ins).|
|Funktioniert mit den Office-Objektmodellen und VBA-APIs.|Ermöglicht den Zugriff sowohl auf die Office-Objektmodelle als auch auf die [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] -APIs.|
|Wurde für die Makroaufzeichnung und einen vereinfachten Entwicklungsprozess konzipiert.|Ist auf Sicherheit, einfachere Codewartung und die Möglichkeit ausgelegt, die vollständige integrierte Entwicklungsumgebung (IDE) von Visual Studio zu verwenden.|
|Eignet sich gut für Lösungen, die von einer engen Integration in Office-Anwendungen profitieren.|Eignet sich gut für Projektmappen, für die alle Ressourcen von Visual Studio und [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]genutzt werden.|
|Verfügt über Einschränkungen für Unternehmen, insbesondere in den Bereichen Sicherheit und Bereitstellung.|Wurde für die Verwendung in Unternehmen konzipiert.|

 Einige Dinge lassen sich mit VBA immer noch mit weniger Aufwand schneller erledigen. Es ist also ratsam, VBA weiterhin für Folgendes zu verwenden:

- Benutzerdefinierte Arbeitsblattfunktionen

- Aufzeichnen von Makros

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Kombinieren von VBA-Lösungen und Office-Lösungen, die mit Visual Studio erstellt wurden
 Sie können VBA-Code aus Office-Projektmappen aufrufen, die mit Visual Studio erstellt wurden, und Sie können auch Code in Office-Projektmappen aus VBA aufrufen, die mit Visual Studio erstellt wurden. Das Verfahren richtet sich jeweils danach, ob es sich bei der Office-Projektmappe um ein VSTO-Add-In oder eine Anpassung auf Dokumentebene handelt. Weitere Informationen finden Sie unter [Abrufen von Code in VSTO-Add-Ins aus anderen Office-](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) Projektmappen und [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Code in VSTO-Add-Ins aus anderen Office-Projektmappen aufzurufen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
