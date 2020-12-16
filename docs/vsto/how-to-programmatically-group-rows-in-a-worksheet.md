---
title: 'Gewusst wie: Programm gesteuertes Gruppieren von Zeilen in einem Arbeitsblatt'
description: Erfahren Sie, wie Sie eine oder mehrere ganze Zeilen in Microsoft Excel Programm gesteuert gruppieren können, indem Sie ein NamedRange-Steuerelement oder ein System eigenes Excel-Bereichs Objekt verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 203ea7d17a02a224c290e5dd3c6070c06a1d26e4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525707"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Gewusst wie: Programm gesteuertes Gruppieren von Zeilen in einem Arbeitsblatt
  Sie können eine oder mehrere ganze Zeilen gruppieren. Um eine Gruppe in einem Arbeitsblatt zu erstellen, verwenden Sie ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein System eigenes Excel-Bereichs Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden eines NamedRange-Steuer Elements
 Wenn Sie ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement einem Projekt auf Dokument Ebene zur Entwurfszeit hinzufügen, können Sie das-Steuerelement verwenden, um eine Gruppe Programm gesteuert zu erstellen. Im folgenden Beispiel wird davon ausgegangen, dass <xref:Microsoft.Office.Tools.Excel.NamedRange> auf demselben Arbeitsblatt drei Steuerelemente vorhanden sind: `data2001` , `data2002` und `dataAll` . Jeder benannte Bereich verweist auf eine ganze Zeile im Arbeitsblatt.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>So erstellen Sie eine Gruppe von Name Drange-Steuerelementen auf einem Arbeitsblatt

1. Gruppieren Sie drei benannte Bereiche, indem Sie die- <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> Methode für jeden Bereich aufrufen. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Um die Gruppierung von Zeilen aufzurufen, wird die- <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> Methode aufgerufen.

## <a name="use-native-excel-ranges"></a>Verwenden von nativen Excel-Bereichen
 Der Code geht davon aus, dass Sie über drei `data2001` Excel `data2002` -Bereiche mit den Namen, und `dataAll` auf einem Arbeitsblatt verfügen.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>So erstellen Sie eine Gruppe von Excel-Bereichen in einem Arbeitsblatt

1. Gruppieren Sie drei benannte Bereiche, indem Sie die- <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> Methode für jeden Bereich aufrufen. Im folgenden Beispiel wird davon ausgegangen, dass es drei Steuer <xref:Microsoft.Office.Interop.Excel.Range> Elemente `data2001` `data2002` mit den Namen, und `dataAll` auf demselben Arbeitsblatt gibt. Jeder benannte Bereich verweist auf eine ganze Zeile im Arbeitsblatt.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Um die Gruppierung von Zeilen aufzurufen, wird die- <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> Methode aufgerufen.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
