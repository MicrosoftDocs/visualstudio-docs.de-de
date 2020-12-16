---
title: 'Gewusst wie: Ändern der Größe von ListObject-Steuerelementen'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Ändern der Größe von ListObject-Steuerelementen in einer Microsoft Excel-Arbeitsmappe verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c401f3938679c72cee3a07c4bff79a5777fcbc1
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528540"
---
# <a name="how-to-resize-listobject-controls"></a>Gewusst wie: Ändern der Größe von ListObject-Steuerelementen
  Sie legen die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements fest, wenn Sie es einer Microsoft Office Excel-Arbeitsmappe hinzufügen. Möglicherweise möchten Sie dessen Größe jedoch zu einem späteren Zeitpunkt ändern. Beispielsweise könnte es sein, dass Sie eine zweispaltige Liste in eine dreispaltige Liste ändern möchten.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit ändern. Sie können die Größe <xref:Microsoft.Office.Tools.Excel.ListObject> von Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt ändern.

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Ändern der Größe von ListObject-Steuerelementen zur Entwurfszeit](#designtime)

- [Ändern der Größe von ListObject-Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene](#runtimedoclevel)

- [Ändern der Größe von ListObject-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelementen finden Sie unter [ListObject Control](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Ändern der Größe eines ListObject-Steuer Elements zur Entwurfszeit
 Sie können die Größe einer Liste ändern, indem Sie auf einen der Ziehpunkte klicken und diesen ziehen oder indem Sie die Größe im Dialogfeld **Größe der Liste ändern** neu definieren.

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>So ändern Sie die Größe einer Liste im Dialogfeld „Größe der Liste ändern“

1. Klicken Sie in der Tabelle auf eine beliebige Stelle  <xref:Microsoft.Office.Tools.Excel.ListObject> . Die Registerkarte Entwurf der **Tabellen Tools**  >   im Menüband wird angezeigt.

2. Klicken Sie im Abschnitt Eigenschaften auf die **Tabelle ändern**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Wählen Sie den neuen Datenbereich für die Tabelle aus.

4. Klicken Sie auf **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ändern der Größe eines ListObject-Steuer Elements zur Laufzeit in einem Projekt auf Dokument Ebene
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zur Laufzeit ändern, indem Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> -Methode verwenden. Mit dieser Methode ist es jedoch nicht möglich, das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement auf eine neue Position auf dem Arbeitsblatt zu verschieben. Die Überschriften müssen in derselben Zeile bleiben, und das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss das ursprüngliche Listenobjekt überlappen. Das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss eine Überschriftenzeile und mindestens eine Zeile mit Daten enthalten.

### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert

1. Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das sich auf **über die Zellen** A1 **bis** B3 `Sheet1`erstreckt.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5** umfasst.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ändern der Größe eines ListObject zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements in jedem beliebigen geöffneten Arbeitsblatt zur Laufzeit ändern. Weitere Informationen zum Hinzufügen eines Steuer Elements <xref:Microsoft.Office.Tools.Excel.ListObject> zu einem Arbeitsblatt mithilfe eines VSTO-Add-Ins finden Sie unter Gewusst [wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert

1. Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das sich auf **über die Zellen** A1 **bis** B3 `Sheet1`erstreckt.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5** umfasst.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject-Steuerelement](../vsto/listobject-control.md)
- [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Gewusst wie: Ändern der Größe von Bookmark-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)
- [Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
