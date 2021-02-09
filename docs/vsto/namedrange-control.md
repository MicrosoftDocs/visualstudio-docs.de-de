---
title: NamedRange-Steuerelement
description: Erfahren Sie, wie das Name Drange-Steuerelement ein Bereich ist, der über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74eb3467c4cfbba5a2cb411a1f0ad439b1a7620b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926624"
---
# <a name="namedrange-control"></a>NamedRange-Steuerelement
  Das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement ist ein Bereich, der über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Erstellen des Steuer Elements
 Sie können <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente einem Microsoft Office Excel-Arbeitsblatt in Projekten auf Dokumentebene zur Entwurfszeit oder zur Laufzeit hinzufügen.

 Sie können einem Arbeitsblatt <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelemente zur Laufzeit in einem VSTO-Add-In hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt standardmäßig nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente können nur Bereiche bestimmter Blätter umfassen. <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente dürfen keine relativen Namen enthalten, die für alle Blätter gelten, und nicht aus Bereichen bestehen, die sich über zwei oder mehrere Arbeitsblätter in einer Arbeitsmappe erstrecken (3D-Bereiche).

## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement
 Ein benannter Bereich erscheint als geeigneter Kandidat für die komplexe Datenbindung, da er mehrere Zellen umfassen kann. Er ist jedoch nichts weiter als eine Ansammlung von Zellen, die keine einfache Zuordnung zwischen einer bestimmten Spalte und einem DataSet ermöglichen. Aus diesem Grund unterstützen <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente nur die einfache Datenbindung. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement kann für die komplexe Datenbindung verwendet werden. Weitere Informationen finden Sie unter [ListObject Control](../vsto/listobject-control.md).

 Das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement kann mithilfe der <xref:System.Windows.Forms.Control.DataBindings%2A> -Eigenschaften an eine Datenquelle gebunden werden. Die Standard-Datenbindungseigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements ist <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.

 Wenn die Daten im gebundenen DataSet auf beliebige Weise aktualisiert werden, spiegelt das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement die Änderungen wider.

## <a name="formatting"></a>Formatierung
 Die gesamte auf <xref:Microsoft.Office.Interop.Excel.Range> anwendbare Formatierung kann auf ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement angewendet werden. Dies umfasst Rahmen, Schriftarten, Zahlenformate und Stile.

## <a name="rename-the-control"></a>Umbenennen des Steuer Elements
 Wenn Sie Ihrem Arbeitsblatt über die <xref:Microsoft.Office.Tools.Excel.NamedRange> Toolbox **ein**-Steuerelement hinzufügen, generiert Visual Studio automatisch einen Namen für das Steuerelement. Sie können diesen Namen im Fenster **Eigenschaften** ändern.

## <a name="events"></a>Ereignisse
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement verfügbar:

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Weitere Informationen
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Exemplarische Vorgehensweise: Program mieren gegen Ereignisse eines NamedRange-Steuer Elements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
