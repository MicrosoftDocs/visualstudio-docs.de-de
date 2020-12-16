---
title: 'Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern'
description: Verwenden Sie Visual Studio, um Microsoft Excel-Arbeitsblätter Programm gesteuert mit dem Arbeitsblatt-Host Element oder der Sheets-Auflistung der Excel-Arbeitsmappe auszuwählen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ddef833feeb4e59f5e9e9b2c95a2170ee3c2530
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528546"
---
# <a name="how-to-programmatically-select-worksheets"></a>Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern
  Die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> wählt das angegebene Objekt aus. Die Auswahl des Benutzers wird in das neue Objekt verschoben. Verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>, wenn Sie den Fokus auf das Objekt verschieben möchten, ohne die Benutzerauswahl zu ändern.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie ein vorhandenes Arbeitsblatt in einem VSTO-Add-in auswählen oder das Arbeitsblatt zur Laufzeit in einer Anpassung auf Dokument Ebene erstellt wurde, müssen Sie mithilfe der Excel-Auflistung der Excel- <xref:Microsoft.Office.Interop.Excel.Sheets> Arbeitsmappe darauf zugreifen. andernfalls können Sie direkt auf das- <xref:Microsoft.Office.Tools.Excel.Worksheet> Host Element zugreifen.

## <a name="use-the-worksheet-host-item"></a>Arbeitsblatt-Host Element verwenden
 Fügen Sie in einer Anpassung auf Dokument Ebene den folgenden Code zu *Sheet1. vb* oder *Sheet1.cs* hinzu.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe eines Hostelements aus

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> -Methode von `Sheet1`auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe
 Greifen Sie auf das Arbeitsblatt mithilfe der Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> zu.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe aus

1. Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf, um das erste Arbeitsblatt der aktiven Arbeitsmappe auszuwählen.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
