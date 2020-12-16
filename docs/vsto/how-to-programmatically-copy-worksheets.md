---
title: 'Vorgehensweise: Programm gesteuertes Kopieren von Arbeitsblättern'
description: Erfahren Sie, wie Sie eine Kopie eines Arbeitsblatts erstellen und dieses Arbeitsblatt vor oder nach einem vorhandenen Arbeitsblatt in der Arbeitsmappe einfügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d4b2f16cfc8855f2adff3a4614c38eb70fbe7db5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524796"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Vorgehensweise: Programm gesteuertes Kopieren von Arbeitsblättern
  Sie können eine Kopie eines Arbeitsblatts erstellen und dieses Arbeitsblatt vor oder hinter einem vorhandenen Arbeitsblatt in der Arbeitsmappe einfügen. Wenn Sie nicht angeben, wo das Arbeitsblatt eingefügt werden soll, erstellt Excel eine neue Arbeitsmappe, die das neue Arbeitsblatt enthält.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Unabhängig davon, ob das Arbeitsblatt programmgesteuert oder vom Endbenutzer manuell kopiert wird, ist kein Code hinter dem neuen Arbeitsblatt vorhanden, und Steuerelemente im neuen Arbeitsblatt funktionieren nicht. Dies liegt daran, dass es sich bei dem neu kopierten Arbeitsblatt um ein <xref:Microsoft.Office.Interop.Excel.Worksheet>-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement handelt. Windows Forms-Steuerelemente und -Hoststeuerelemente können nur Hostelementen hinzugefügt werden. Weitere Informationen finden Sie Unterprogramm gesteuerte [Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einer Anpassung auf Dokumentebene hinzu

1. Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.

     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einem VSTO-Add-In hinzu

1. Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Vorgehensweise: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
