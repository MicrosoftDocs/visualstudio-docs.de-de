---
title: XmlMappedRange-Steuerelement
description: Erfahren Sie, dass es sich bei dem XmlMappedRange-Steuerelement um einen Bereich handelt, der nur erstellt wird, wenn ein nicht wiederholtes Schema Element einer Zelle in Microsoft Excel zugeordnet ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2849b815c38555be6b149544bb9d9953fe85ec4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894399"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange-Steuerelement
  Das- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement ist ein Bereich, der nur erstellt wird, wenn ein nicht wiederholtes Schema Element einer Zelle in Microsoft Office Excel zugeordnet wird. Dies ist beispielsweise der Fall, wenn das- `maxOccurs` Attribut eines Schema Elements 1 ist. Nachdem der von Visual Studio zugeordnete XML-Bereich erstellt wurde, können Sie ihn direkt programmieren, ohne das Excel-Objektmodell durchlaufen zu müssen. Sie können ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement nur in Excel löschen, wenn die Element Zuordnung entfernt wird.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement
 Ein- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement unterstützt das Binden an ein einzelnes Datenfeld (einfache Datenbindung). Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement kann eine komplexe Datenbindung unterstützen und wird automatisch erstellt, wenn ein sich wiederholendes Schema Element einer Zelle zugeordnet wird. Weitere Informationen finden Sie unter [ListObject Control](../vsto/listobject-control.md).

 Das- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement wird mithilfe der-Eigenschaft an eine Datenquelle gebunden <xref:System.Windows.Forms.Control.DataBindings%2A> . Wenn eine einer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Arbeitsblatt Zelle hinzugefügt wird, generiert Visual Studio automatisch ein DataSet aus den Daten in den zugeordneten Zellen und bindet das Steuerelement an dieses DataSet. Die Standard-Daten Bindungs Eigenschaft des <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ist <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Wenn die Daten im gebundenen Dataset durch einen beliebigen Mechanismus aktualisiert werden, spiegelt das- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement die Änderungen wider.

## <a name="formatting"></a>Formatierung
 Sie können die gleiche Formatierung auf ein Steuerelement anwenden <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , das Sie auf ein anwenden können <xref:Microsoft.Office.Interop.Excel.Range> . Dies umfasst, Rahmen, Schriftarten, Zahlenformate und Stile.

## <a name="events"></a>Ereignisse
 Folgende Ereignisse sind für das-Steuerelement verfügbar <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> :

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Weitere Informationen
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Gewusst wie: Hinzufügen von XmlMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
