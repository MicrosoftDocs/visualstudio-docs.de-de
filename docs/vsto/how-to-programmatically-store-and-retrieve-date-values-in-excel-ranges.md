---
title: Speichern & Programm gesteuertes Abrufen von Datums Werten in Excel-Bereichen
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Datumswerte in Microsoft Excel-Bereichen Programm gesteuert zu speichern und abzurufen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 892f8db0a6cbeee485c8139c2d6e4614f17c1cc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899403"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Vorgehensweise: Programm gesteuertes speichern und Abrufen von Datums Werten in Excel-Bereichen
  Sie können Werte in einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder einem systemeigenen Excel-Bereichs Objekt speichern und abrufen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie einen Datumswert, der in einem Bereich oder nach 1/1/1900 liegt, mithilfe von Office-Entwicklungs Tools in Visual Studio speichern, wird er im OA-Format (OLE Automation) gespeichert. Sie müssen die- <xref:System.DateTime.FromOADate%2A> Methode verwenden, um den Wert von OLE-Automatisierungsdaten (OA) abzurufen. Wenn das Datum vor 1/1/1900 liegt, wird es als Zeichenfolge gespeichert.

> [!NOTE]
> Excel-Datumsangaben unterscheiden sich von OLE-Automatisierungsdaten für die ersten beiden Monate 1900. Es gibt auch Unterschiede, wenn die Option " **1904 Date System** " aktiviert ist. In den folgenden Codebeispielen werden diese Unterschiede nicht behandelt.

## <a name="use-a-namedrange-control"></a>Verwenden eines NamedRange-Steuer Elements

- Dieses Beispiel gilt für Anpassungen auf Dokument Ebene. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der- `ThisWorkbook` Klasse.

### <a name="to-store-a-date-value-in-a-named-range"></a>So speichern Sie einen Datumswert in einem benannten Bereich

1. Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement in Zelle **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Legen Sie das heutige Datum als Wert für fest `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>So rufen Sie einen Datumswert aus einem benannten Bereich ab

1. Rufen Sie den Datumswert aus ab `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Verwenden von nativen Excel-Bereichen

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>So speichern Sie einen Datumswert in einem systemeigenen Excel-Bereichs Objekt

1. Erstellen Sie einen <xref:Microsoft.Office.Interop.Excel.Range> , der die Zelle **a1** darstellt.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Legen Sie das heutige Datum als Wert für fest `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>So rufen Sie einen Datumswert aus einem systemeigenen Excel-Bereichs Objekt ab

1. Rufen Sie den Datumswert aus ab `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
