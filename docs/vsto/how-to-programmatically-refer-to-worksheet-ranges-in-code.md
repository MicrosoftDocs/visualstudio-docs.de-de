---
title: 'Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Programm gesteuert auf den Inhalt eines NamedRange-Steuer Elements oder eines systemeigenen Excel-Bereichs Objekts in einem Microsoft Excel-Arbeitsblatt zu verweisen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89a4b7c594f942405777145f94ed0a3503e9b16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963756"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code
  Sie verwenden einen ähnlichen Prozess, um auf den Inhalt eines <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuer Elements oder eines systemeigenen Excel-Bereichs Objekts zu verweisen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden eines NamedRange-Steuer Elements
 Im folgenden Beispiel wird ein einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Arbeitsblatt hinzugefügt, und dann wird der Zelle im Bereich Text hinzugefügt.

### <a name="to-refer-to-a-namedrange-control"></a>So verweisen Sie auf ein Name Drange-Steuerelement

1. Weisen Sie der-Eigenschaft des-Steuer Elements eine Zeichenfolge zu <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> . Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Verwenden von nativen Excel-Bereichen
 Im folgenden Beispiel wird einem Arbeitsblatt ein nativer Excel-Bereich hinzugefügt und dann der Zelle im Bereich Text hinzugefügt.

### <a name="to-refer-to-a-native-range-object"></a>So verweisen Sie auf ein System eigenes Bereichs Objekt

1. Weisen Sie der-Eigenschaft des Bereichs eine Zeichenfolge zu <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> .

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Gewusst wie: Programm gesteuertes automatisches Auffüllen von Bereichen mit inkrementellen Änderungs Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Gewusst wie: Programm gesteuertes suchen nach Text in Arbeitsblatt Bereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
