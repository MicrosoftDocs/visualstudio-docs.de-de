---
title: Ändern von Formaten in Zeilen, die ausgewählte Zellen durch Code enthalten
description: Erfahren Sie, wie Sie die Schriftart einer gesamten Zeile ändern können, die eine ausgewählte Zelle enthält, sodass der Text fett formatiert ist.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62b9f94bfa423b149fef6abb984a03536d0e3d8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875314"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Gewusst wie: Programm gesteuertes Ändern der Formatierung in Arbeitsblatt Zeilen, die ausgewählte Zellen enthalten
  Sie können die Schriftart einer gesamten Zeile, die eine ausgewählte Zelle enthält, so ändern, dass der Text fett formatiert ist.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>So machen Sie die aktuelle Zeile fett und die zuvor Fett formatierte Zeile normal

1. Deklarieren Sie eine statische Variable, um die zuvor ausgewählte Zeile nachzuverfolgen.

    [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
    [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]

2. Rufen Sie mithilfe der-Eigenschaft einen Verweis auf die aktuelle Zelle ab <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> .

    [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
    [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]

3. Formatieren Sie die aktuelle Zeile mit der- <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> Eigenschaft der aktiven Zelle fett.

    [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
    [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]

4. Stellen Sie sicher, dass der aktuelle Wert von `previousRow` nicht 0 ist. Ein Wert von 0 (null) gibt an, dass dies das erste Mal in diesem Code ist.

    [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
    [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]

5. Stellen Sie sicher, dass sich die aktuelle Zeile von der vorherigen Zeile unterscheidet.

    [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
    [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]

6. Rufen Sie einen Verweis auf einen Bereich ab, der die zuvor ausgewählte Zeile darstellt, und legen Sie fest, dass diese Zeile nicht fett formatiert ist.

    [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
    [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]

7. Speichert die aktuelle Zeile, sodass Sie beim nächsten Durchlauf zur vorherigen Zeile werden kann.

    [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
    [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]

   Das folgende Beispiel zeigt die vollständige Methode.

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Gewusst wie: Programm gesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
