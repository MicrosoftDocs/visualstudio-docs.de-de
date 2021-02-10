---
title: 'Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen'
description: Erfahren Sie, wie Sie ein Arbeitsblatt in einer Microsoft Excel-Arbeitsmappe Programm gesteuert mithilfe des Arbeitsblatt-Host Elements löschen können, z. b..
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2289309932dcd1d946fc775de60a0e07892be222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963891"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen
  Sie können jedes beliebige Arbeitsblatt in einer Arbeitsmappe löschen. Verwenden Sie zum Löschen eines Arbeitsblatts das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Arbeitsblatt-Host Element verwenden
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>, um ein angegebenes Arbeitsblatt zu löschen. Der folgende Code löscht ein Arbeitsblatt aus einer Arbeitsmappe durch direktes Verweisen auf das Arbeitsblatt-Hostelement.

> [!IMPORTANT]
> Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:
>
> - Excel 2013-Arbeitsmappe
> - Excel 2013-Vorlage
> - Excel 2010-Arbeitsmappe
> - Excel 2010-Vorlage
>
>   Wenn Sie diese Aufgabe in einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft. Office. Interop. Excel** -Assembly hinzufügen. Anschließend müssen Sie Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe zu öffnen und ein Arbeitsblatt zu löschen. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) -Assemblys und [Referenz zur primären Interopassembly für Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>So löschen Sie ein Arbeitsblatt mithilfe eines Arbeitsblatt-Hostelements

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> -Methode von `Sheet1`auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:

- Sie möchten ein Arbeitsblatt in einem VSTO-Add-In löschen.

- Das Arbeitsblatt, das Sie löschen möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.

  Der folgende Code löscht ein Arbeitsblatt aus einer-Arbeitsmappe, indem auf das Blatt durch die Indexnummer der **Sheets** -Auflistung verwiesen wird. Dieser Code geht davon aus, dass ein neues Arbeitsblatt programmgesteuert erstellt wurde.

> [!IMPORTANT]
> Wenn Sie diese Aufgabe in einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft. Office. Interop. Excel** -Assembly hinzufügen. Anschließend müssen Sie Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe zu öffnen und ein Arbeitsblatt zu löschen. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) -Assemblys und [Referenz zur primären Interopassembly für Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>So löschen Sie ein Arbeitsblatt mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe

1. Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](how-to-programmatically-hide-worksheets.md)
- [Gewusst wie: Programm gesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern](how-to-programmatically-select-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Arbeitsblatt-Host Element](worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](global-access-to-objects-in-office-projects.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](programmatic-limitations-of-host-items-and-host-controls.md)
