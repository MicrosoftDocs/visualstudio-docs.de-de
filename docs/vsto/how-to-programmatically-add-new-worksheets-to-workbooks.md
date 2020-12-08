---
title: 'Vorgehensweise: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen'
description: Erfahren Sie, wie Sie ein Arbeitsblatt Programm gesteuert erstellen und das Arbeitsblatt dann zur Auflistung der Arbeitsblätter in der Arbeitsmappe hinzufügen können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3397b2ad8f656a7ada82ce0be17dcf21064d0ee3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96843983"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Vorgehensweise: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen
  Sie können ein Arbeitsblatt programmgesteuert erstellen und das Arbeitsblatt dann zur Auflistung der Arbeitsblätter in der Arbeitsmappe hinzufügen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>So fügen Sie einer Arbeitsmappe in einer Anpassung auf Dokumentebene ein neues Arbeitsblatt hinzu

1. Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Sheets> -Auflistung.

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement hinzufügen möchten, sollten Sie das Arbeitsblatt zur Entwurfszeit hinzufügen.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>So fügen Sie einer Arbeitsmappe ein neues Arbeitsblatt in einem VSTO-Add-In hinzu

1. Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Sheets> -Auflistung.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Sie können auch ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement vom systemeigenen <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt generieren. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
