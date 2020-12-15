---
title: 'Gewusst wie: Programm gesteuertes Sortieren von Daten in Arbeitsblättern'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Sortieren von Daten verwenden können, die in Arbeitsblatt Bereichen und Listen zur Laufzeit enthalten sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f09fed7f1caff68a485d9d0d98789555ec30889c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523685"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Gewusst wie: Programm gesteuertes Sortieren von Daten in Arbeitsblättern
  Sie können Daten sortieren, die zur Laufzeit in Arbeitsblattbereichen und -listen enthalten sind. Der folgende Code sortiert einen mehrspaltigen Bereich namens `Fruits` nach den Daten in der ersten Spalte und anschließend nach den Daten in der zweiten Spalte.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Sortieren von Daten in einer Anpassung auf Dokument Ebene

### <a name="to-sort-data-in-a-namedrange-control"></a>So sortieren Sie Daten in einem NamedRange-Steuerelement

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A>-Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelements auf. Das folgende Beispiel erfordert ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement namens `Fruits` in einem Arbeitsblatt. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]

   Platzieren Sie den folgenden Code in *Sheet1. vb* oder *Sheet1.cs* , um die Daten in einem-Steuerelement zu sortieren <xref:Microsoft.Office.Tools.Excel.ListObject> . Der Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.ListObject>-Steuerelement namens `fruitList`in einem Arbeitsblatt namens `Sheet1` verfügen.

### <a name="to-sort-data-in-a-listobject-control"></a>So sortieren Sie Daten in einem ListObject-Steuerelement

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>-Eigenschaft des <xref:Microsoft.Office.Tools.Excel.ListObject>-Hoststeuerelements auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]

## <a name="sort-data-in-a-vsto-add-in"></a>Sortieren von Daten in einem VSTO-Add-in

### <a name="to-sort-data-in-a-native-range"></a>So sortieren Sie Daten in einem systemeigenen Bereich

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode des systemeigenen Excel-<xref:Microsoft.Office.Interop.Excel.Range>-Steuerelements auf. Das folgende Beispiel erfordert ein systemeigenes Excel-Steuerelement namens `Fruits` in einem Arbeitsblatt.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]

### <a name="to-sort-data-in-a-listobject-control"></a>So sortieren Sie Daten in einem ListObject-Steuerelement

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>-Eigenschaft des systemeigenen Excel-<xref:Microsoft.Office.Interop.Excel.ListObject>-Steuerelements auf. Im folgenden Beispiel wird vorausgesetzt, dass Sie über ein systemeigenes Excel-<xref:Microsoft.Office.Interop.Excel.ListObject>-Steuerelement namens `fruitList` im aktiven Arbeitsblatt verfügen.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes automatisches Auffüllen von Bereichen mit inkrementellen Änderungs Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [ListObject-Steuerelement](../vsto/listobject-control.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
