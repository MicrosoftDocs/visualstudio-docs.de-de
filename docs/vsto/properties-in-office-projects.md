---
title: Eigenschaften in Office-Projekten
description: Erfahren Sie mehr über die Eigenschaften, die für Office-Projekte in Visual Studio über das Eigenschaftenfenster verfügbar sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdc54de3935646e36f9d4f09727037de4c373c92
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528027"
---
# <a name="properties-in-office-projects"></a>Eigenschaften in Office-Projekten
  Es gibt mehrere wichtige Eigenschaften, die für Office-Projekte in Visual Studio verfügbar sind. Sie können auf diese Eigenschaften über das Fenster **Eigenschaften** zugreifen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Namespace für Host Element
 Verwenden Sie die Eigenschaft **Namespace für Host Element** , um den Namespace für Host Element Klassen (z. b `ThisAddIn` `ThisWorkbook` . die Klassen, oder `ThisDocument` ) in Visual c#-Projekten zu ändern. Diese Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn Sie den Dokument Knoten in einem Projekt auf Dokument Ebene (z. b. *ExcelWorkbook1.xlsx* oder *WordDocument1.docx*) oder den Anwendungs Knoten in einem VSTO-Add-in-Projekt (z. b. Excel oder Word) in **Projektmappen-Explorer** auswählen.

 Wenn Sie ein Visual C#-Office-Projekt erstellen, erhalten Hostelemente einen Namespace, der auf dem Namen des Projekts basiert. Es wird empfohlen, die Eigenschaft **Namespace für Hostelement** zu verwenden, um den Namespace zu ändern, anstatt die Codedateien direkt zu bearbeiten. Wenn Sie diese Eigenschaft verwenden, wird der Namespace in den generierten (ausgeblendeten) Codedateien und in den sichtbaren Codedateien geändert.

## <a name="cacheindocument"></a>CacheInDocument
 Die **CacheInDocument** -Eigenschaft wird im Fenster **Eigenschaften** für Projekte der Dokumentebene angezeigt, wenn Sie eine Instanz von <xref:System.Data.DataSet> im Visual Studio-Designer auswählen. Nur öffentliche Member können zwischengespeichert werden. Stellen Sie sicher, dass die **Modifiers** -Eigenschaft auf **Public** festgelegt ist, wenn Sie ein <xref:System.Data.DataSet>-Element zwischenspeichern möchten.

 Diese Eigenschaft verwendet einen booleschen Wert:

- Wählen Sie **true** , um das DataSet im Dokument zwischenzuspeichern.

- Wählen Sie **false** , wenn Sie das DataSet nicht im Dokument zwischenspeichern möchten.

  Weitere Informationen zum Zwischenspeichern von Daten finden Sie unter [zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Wert2
 Die **Value2** -Eigenschaft ist nur für Excel-Arbeitsmappen oder Vorlagenprojekte verfügbar. Sie wird im Fenster **Eigenschaften** unter dem Eigenschaftenknoten **Databindings** angezeigt, wenn Sie im Arbeitsblatt-Designer ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auswählen.

 Verwenden Sie die **Value2** -Eigenschaft im Fenster **Eigenschaften** , um die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Elements an ein Feld in Ihrer Datenquelle zu binden.

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
- [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md)
