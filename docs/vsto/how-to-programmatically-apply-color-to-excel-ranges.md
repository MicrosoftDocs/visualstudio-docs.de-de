---
title: 'Gewusst wie: Programm gesteuertes Anwenden von Farben auf Excel-Bereiche'
description: Erfahren Sie, wie Sie ein Name Drange-Steuerelement oder ein System eigenes Excel-Bereichs Objekt verwenden, um eine Farbe auf den Text in einem Zellen Bereich anzuwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63a38bb4fb6f8f8ab35b9e1104a1b93d6d757446
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848000"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Gewusst wie: Programm gesteuertes Anwenden von Farben auf Excel-Bereiche
  Verwenden Sie ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein System eigenes Excel-Bereichs Objekt, um eine Farbe auf Text in einem Zellen Bereich anzuwenden.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden eines NamedRange-Steuer Elements
 Dieses Beispiel gilt für Anpassungen auf Dokument Ebene.

### <a name="to-apply-color-to-a-namedrange-control"></a>So wenden Sie eine Farbe auf ein Name Drange-Steuerelement an

1. Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement in Zelle a1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Legen Sie die Farbe des Texts im- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Verwenden von nativen Excel-Bereichen

### <a name="to-apply-color-to-a-native-excel-range-object"></a>So wenden Sie eine Farbe auf ein System eigenes Excel-Bereichs Objekt an

1. Erstellen Sie einen Bereich in Zelle a1, und legen Sie dann die Farbe des Texts fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
