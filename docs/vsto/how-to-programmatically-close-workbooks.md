---
title: 'Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen'
description: Erfahren Sie, wie Sie die aktive Arbeitsmappe schließen können, oder Sie können eine Arbeitsmappe angeben, die Programm gesteuert geschlossen werden soll.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4bec2cbbe0cb2a57ec2373bd220abc49dabc5bfb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903676"
---
# <a name="how-to-programmatically-close-workbooks"></a>Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen
  Sie können die aktive Arbeitsmappe schließen, oder eine Arbeitsmappe angeben, die geschlossen werden soll.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Schließen der aktiven Arbeitsmappe
 Es gibt zwei Verfahren zum Schließen der aktiven Arbeitsmappe: eine für Anpassungen auf Dokumentebene und eine für VSTO-Add-Ins.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>So schließen Sie die aktive Arbeitsmappe in einer Anpassung auf Dokumentebene

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> -Methode auf, um die der Anpassung zugeordnete Arbeitsmappe zu schließen. Um das folgende Codebeispiel zu verwenden, führen sie es in der `Sheet1` -Klasse in einem Projekt auf Dokumentebene für Excel aus.

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>So schließen Sie die aktive Arbeitsmappe in einem VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> -Methode auf, um die aktive Arbeitsmappe zu schließen. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>Eine Arbeitsmappe, die Sie anhand des Namens angeben, schließen
 Das Schließen einer namentlich angegebenen Arbeitsmappe erfolgt bei VSTO-Add-Ins und Anpassungen auf Dokumentebene auf die gleiche Weise.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>So schließen Sie eine namentlich angegebene Arbeitsmappe

1. Geben Sie den Namen der Arbeitsmappe als Argument für die <xref:Microsoft.Office.Interop.Excel.Workbooks> -Auflistung an. Im folgenden Codebeispiel wird davon ausgegangen, dass eine Arbeitsmappe mit dem Namen **NewWorkbook** in Excel geöffnet ist.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
