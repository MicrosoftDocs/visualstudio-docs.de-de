---
title: 'Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern'
description: Erfahren Sie, wie Sie die Schreibweise von Wörtern in einem Microsoft Excel-Arbeitsblatt Programm gesteuert überprüfen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94361db98c78a2767680d2358d2153b63df9571a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867983"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern
  Sie können die Rechtschreibung von Wörtern in einem Arbeitsblatt programmgesteuert überprüfen. Das Dialogfeld **Rechtschreibung** wird automatisch angezeigt wird, wenn das Arbeitsblatt falsch geschriebene Wörter enthält.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>So führen Sie die Rechtschreibprüfung in einer Anpassung auf Dokumentebene aus

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> -Methode des Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>So überprüfen Sie die Rechtschreibung in einem Arbeitsblatt in einem VSTO-Add-in

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> -Methode des aktiven Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
