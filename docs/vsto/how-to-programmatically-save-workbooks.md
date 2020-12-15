---
title: 'Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen'
description: Programm gesteuertes Speichern von Microsoft Excel-Arbeitsmappen, ohne den Pfad zu ändern und eine Kopie einer Arbeitsmappe zu speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbc228a703d6c9224fda545a93132ccb45c94b0f
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524619"
---
# <a name="how-to-programmatically-save-workbooks"></a>Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen
  Es gibt mehrere Möglichkeiten, eine Arbeitsmappe zu speichern. Sie können eine Arbeitsmappe speichern, ohne den Pfad zu ändern. Wenn die Arbeitsmappe noch nicht gespeichert wurde, sollten Sie sie unter Angabe eines Pfads speichern. Ohne expliziten Pfad speichert Microsoft Office Excel die Datei unter dem bei der Erstellung angegebenen Namen im aktuellen Ordner. Sie können auch eine Kopie der Arbeitsmappe speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Arbeitsmappe speichern, ohne den Pfad zu ändern

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> -Methode der `ThisWorkbook` -Klasse auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>-Methode auf, um die aktive Arbeitsmappe zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]

## <a name="save-a-workbook-with-a-new-path"></a>Speichern einer Arbeitsmappe unter einem neuen Pfad
 Sie können die angegebene Arbeitsmappe an einem neuen Speicherort oder unter einem neuen Namen speichern und optional ein Dateiformat, ein Kennwort, einen Zugriffsmodus und mehr angeben.

> [!NOTE]
> Möglicherweise möchten Sie die- <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> Eigenschaft auf **false** festlegen, bevor Sie die Arbeitsmappe mit einem neuen Pfad speichern, da das Speichern in einigen Formaten eine Interaktion erfordert. Das Festlegen dieser Eigenschaft auf **false** bewirkt, dass Excel alle Standardwerte verwendet.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> -Methode der `ThisWorkbook` -Klasse auf. Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`-Klasse aus.

     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>-Methode auf, um die aktive Arbeitsmappe unter einem neuen Pfad zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]

## <a name="save-a-copy-of-the-workbook"></a>Speichern Sie eine Kopie der Arbeitsmappe.
 Sie können eine Kopie der Arbeitsmappe in einer Datei speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern. Dies ist hilfreich, wenn Sie eine Sicherungskopie erstellen möchten, ohne den Speicherort der Arbeitsmappe zu ändern.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> -Methode der `ThisWorkbook` -Klasse auf. Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`-Klasse aus.

     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>-Methode auf, um eine Kopie der aktiven Arbeitsmappe zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn eine der Methoden, mit der die Arbeitsmappe gespeichert oder kopiert wird, interaktiv abgebrochen wird, wird ein Laufzeitfehler im Code ausgelöst. Wenn Ihre Prozedur z. b. die-Methode aufruft, <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> aber keine Eingabe Aufforderungen von Excel deaktiviert und der Benutzer bei entsprechender Aufforderung auf **Abbrechen** klickt, löst Excel einen Laufzeitfehler aus.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)
- [Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
