---
title: 'Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern'
description: Erfahren Sie, wie Sie mit dem Arbeitsblatt-Host Element ein Arbeitsblatt in einer Microsoft Excel-Arbeitsmappe Programm gesteuert anzeigen oder ausblenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a5ba61c7db0a62cf3e97fb8e4df5cb655e9f2dd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525669"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern
  Sie können jedes Arbeitsblatt in einer Arbeitsmappe anzeigen oder ausblenden. Wenn Sie ein Arbeitsblatt ausblenden möchten, verwenden Sie das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Arbeitsblatt-Host Element verwenden
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft, um das angegebene Arbeitsblatt auszublenden.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>So blenden Sie ein Arbeitsblatt mit einem Worksheet-Hostelement aus

1. Legen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft des `Sheet1` -Hostelements auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:

- Sie möchten ein Arbeitsblatt in einem VSTO-Add-in ausblenden.

- Das Arbeitsblatt, das Sie ausblenden möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>So blenden Sie ein Arbeitsblatt mit der Sheets-Auflistung der Excel-Arbeitsmappe aus

1. Legen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> -Eigenschaft des Arbeitsblatts auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Gewusst wie: Programm gesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
