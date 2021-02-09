---
title: 'Gewusst wie: Programm gesteuertes hinzufügen und Löschen von Arbeitsblatt Kommentaren'
description: Erfahren Sie, wie Sie Kommentare in Microsoft Office Excel-Arbeitsblättern Programm gesteuert hinzufügen und löschen können. Sie können nur einzelnen Zellen Kommentare hinzufügen, nicht zu Bereichen mit mehreren Zellen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec70c03dfdce05c7445762e2cfd452f3fdf90775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904489"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Gewusst wie: Programm gesteuertes hinzufügen und Löschen von Arbeitsblatt Kommentaren
  Sie können Kommentare in Microsoft Office Excel-Arbeitsblättern programmgesteuert hinzufügen und löschen. Kommentare können nur einzelnen Zellen, nicht Bereichen mit mehreren Zellen hinzugefügt werden.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Hinzufügen und Löschen eines Kommentars in einem Projekt auf Dokument Ebene
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `dateComment` auf dem Arbeitsblatt `Sheet1`befindet.

### <a name="to-add-a-new-comment-to-a-named-range"></a>So fügen Sie einem benannten Bereich einen neuen Kommentar hinzu

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> -Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements auf, und geben Sie den Kommentartext an. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>So löschen Sie einen Kommentar aus einem benannten Bereich

1. Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Hinzufügen und Löschen eines Kommentars in einem VSTO-Add-in-Projekt
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelement namens `dateComment` auf dem aktiven Arbeitsblatt befindet.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>So fügen Sie einem Excel-Bereich einen neuen Kommentar hinzu

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> -Methode des <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelements auf, und stellen Sie den Kommentartext bereit.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>So löschen Sie einen Kommentar aus einem Excel-Bereich

1. Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Anzeigen von Arbeitsblatt Kommentaren](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
