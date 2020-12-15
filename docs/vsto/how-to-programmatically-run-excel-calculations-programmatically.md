---
title: 'Gewusst wie: Programm gesteuertes Ausführen von Excel-Berechnungen'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Ausführen von Berechnungen in einer Microsoft Excel-Arbeitsmappe verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9f385e7c58972844c30320c680f42d8394580d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524696"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Gewusst wie: Programm gesteuertes Ausführen von Excel-Berechnungen
  Sie verwenden einen ähnlichen Prozess zum Ausführen von Berechnungen in einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder einem systemeigenen Excel-Bereichs Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Ausführen von Berechnungen in einem Name Drange-Steuerelement
 Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange> in Zelle a1 erstellt und dann die Zelle berechnet. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

### <a name="to-run-calculations-in-a-namedrange-control"></a>So führen Sie Berechnungen in einem Name Drange-Steuerelement aus

1. Erstellen Sie den benannten Bereich.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Ruft die- <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> Methode des angegebenen Bereichs auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Ausführen von Berechnungen in einem nativen Excel-Bereich

### <a name="to-run-calculations-in-a-native-excel-range"></a>So führen Sie Berechnungen in einem nativen Excel-Bereich aus

1. Erstellen Sie den benannten Bereich.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Ruft die- <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> Methode des angegebenen Bereichs auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
