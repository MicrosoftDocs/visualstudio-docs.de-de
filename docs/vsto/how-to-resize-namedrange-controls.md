---
title: 'Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Ändern der Größe von Name Drange-Steuerelementen in einer Microsoft Excel-Arbeitsmappe verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043def019d30ee629e672a081cd5aea73bca4304
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528181"
---
# <a name="how-to-resize-namedrange-controls"></a>Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen
  Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements festlegen, wenn Sie es zu einem Microsoft Office Excel-Dokument hinzufügen. Möglicherweise möchten Sie jedoch zu einem späteren Zeitpunkt die Größe ändern.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Sie können einen benannten Bereich in Projekten auf Dokumentebene zur Entwurfszeit oder zur Laufzeit ändern. Sie können benannte Bereiche in VSTO-Add-Ins auf Anwendungsebene auch zur Laufzeit ändern.

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Ändern der Größe von Name Drange-Steuerelementen zur Entwurfszeit](#designtime)

- [Ändern der Größe von Name Drange-Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene](#runtimedoclevel)

- [Ändern der Größe von Name Drange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Ändern der Größe von Name Drange-Steuerelementen zur Entwurfszeit
 Sie können die Größe eines benannten Bereichs ändern, indem Sie die Größe im Dialogfeld **Namen definieren** neu definieren.

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>So ändern Sie die Größe eines benannten Bereichs unter Verwendung des Dialogfelds „Namen definieren“

1. Klicken Sie mit der rechten Maustaste auf ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement.

2. Klicken Sie im Kontextmenü auf **Benannte Bereiche verwalten** .

     Das Dialogfeld **Namen definieren** wird geöffnet.

3. Wählen Sie den benannten Bereich aus, dessen Größe Sie ändern möchten.

4. Deaktivieren Sie das Feld **Bezieht sich auf** .

5. Wählen Sie die Zellen aus, anhand derer Sie die Größe des benannten Bereichs definieren möchten.

6. Klicken Sie auf **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ändern der Größe von Name Drange-Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene
 Sie können die Größe eines benannten Bereichs programmgesteuert ändern, indem Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> -Eigenschaft verwenden.

> [!NOTE]
> Im Fenster **Eigenschaften** ist die <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> -Eigenschaft als schreibgeschützt markiert.

### <a name="to-resize-a-named-range-programmatically"></a>So ändern Sie die Größe eines benannten Bereichs programmgesteuert

1. Erstellen Sie in der Zelle <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 **von** ein `Sheet1`-Steuerelement.

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Ändern Sie die Größe des benannten Bereichs, sodass er auch Zelle **B1** umfasst.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ändern der Größe von Name Drange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements in jedem beliebigen geöffneten Arbeitsblatt zur Laufzeit ändern. Weitere Informationen zum Hinzufügen eines Steuer Elements <xref:Microsoft.Office.Tools.Excel.NamedRange> zu einem Arbeitsblatt mithilfe eines VSTO-Add-Ins finden Sie unter Gewusst [wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>So ändern Sie die Größe eines benannten Bereichs programmgesteuert

1. Erstellen Sie in der Zelle <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 **von** ein `Sheet1`-Steuerelement.

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Ändern Sie die Größe des benannten Bereichs, sodass er auch Zelle **B1** umfasst.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Gewusst wie: Ändern der Größe von Bookmark-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)
- [Gewusst wie: Ändern der Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)
