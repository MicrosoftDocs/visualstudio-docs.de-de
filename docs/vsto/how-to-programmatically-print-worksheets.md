---
title: 'Vorgehensweise: Programm gesteuertes Drucken von Arbeitsblättern'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um alle Arbeitsblätter in einer Microsoft Excel-Arbeitsmappe Programm gesteuert zu drucken.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523766"
---
# <a name="how-to-programmatically-print-worksheets"></a>Vorgehensweise: Programm gesteuertes Drucken von Arbeitsblättern

Sie können beliebige Arbeitsblätter aus einer Arbeitsmappe drucken.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drucken eines Arbeitsblatts in einer Anpassung auf Dokument Ebene

### <a name="to-print-a-worksheet"></a>So drucken Sie ein Arbeitsblatt

1. Rufen Sie die `PrintOut`-Methode von `Sheet1` auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   Mit der- <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Methode können Sie das angegebene Objekt im Seiten  Ansichts Fenster anzeigen. Der folgende Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement namens `Sheet1` verfügen.

### <a name="to-preview-a-page-before-printing"></a>So zeigen Sie eine Vorschau der Seite vor dem Druck an

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> -Methode des Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drucken eines Arbeitsblatts in einem VSTO-Add-in

### <a name="to-print-a-worksheet"></a>So drucken Sie ein Arbeitsblatt

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A>-Methode des aktiven Arbeitsblatts auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   Mit der- <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Methode können Sie das angegebene Objekt im Seiten  Ansichts Fenster anzeigen.

### <a name="to-preview-a-page-before-printing"></a>So zeigen Sie eine Vorschau der Seite vor dem Druck an

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> -Methode des aktiven Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
