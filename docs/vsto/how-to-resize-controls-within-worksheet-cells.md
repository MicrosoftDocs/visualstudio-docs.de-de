---
title: 'Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2d22973e13ee77b66de303041f8b6a765b4b93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545872"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen
  Wenn Sie die Größe von Spalten oder Zeilen in einem Arbeitsblatt ändern, werden alle Host Steuerelemente in den Zellen automatisch an die Höhe oder Breite der Zelle angepasst, deren Größe geändert wurde. Die Größe Windows Forms Steuerelemente wird standardmäßig nicht automatisch geändert.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Wenn Sie die Steuerelemente zur Entwurfszeit hinzufügen, müssen Sie für jedes Steuerelement Positionierungs Optionen festlegen.

 Wenn Sie ein Windows Forms-Steuerelement Programm gesteuert hinzufügen und ein Range-Argument angeben, wird das Steuerelement automatisch angepasst, wenn die Größe einer Zelle innerhalb des Bereichs geändert wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Ändern der Größe von Steuerelementen zur Entwurfszeit

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>So ändern Sie die Größe von Steuerelementen zur Entwurfszeit mit Zellen

1. Ziehen Sie ein Windows Forms-Steuerelement aus der **Toolbox**auf ein Arbeitsblatt.

2. Klicken Sie mit der rechten Maustaste auf das Steuerelement, und klicken Sie dann auf **Format Control**

3. Klicken Sie im Dialogfeld **Format Steuer** Element auf die Registerkarte **Eigenschaften** .

4. Wählen Sie unter **Objekt Positionierung**die Option **verschieben und Größe mit Zellen** aus, und klicken Sie dann auf **OK**.

     Wenn Sie die Größe der Zelle ändern, die das Steuerelement enthält, wird die Größe des Steuer Elements an die Zelle angepasst.

## <a name="resize-controls-at-run-time"></a>Ändern der Größe von Steuerelementen zur Laufzeit
 Wenn Sie ein Windows Forms-Steuerelement zur Laufzeit hinzufügen und ein <xref:Microsoft.Office.Interop.Excel.Range> als Speicherort für das-Steuerelement übergeben, wird die Größe des Steuer Elements automatisch geändert, wenn die Arbeitsblatt Zelle, die den Bereich enthält, in der Größe geändert wird.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>So ändern Sie die Größe der Steuerelemente mit Zellen zur Laufzeit

1. Fügen Sie dem Bereich a1 ein Steuerelement hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Wenn Sie die Größe der Zelle ändern, die das Steuerelement enthält, wird die Größe des Steuer Elements an die Zelle angepasst.

## <a name="reset-control-placement"></a>Steuerelement Platzierung zurücksetzen
 Sie können die Platzierung und die Größe des Steuer Elements zurücksetzen, indem Sie die- `Placement` Eigenschaft auf einen der folgenden <xref:Microsoft.Office.Interop.Excel.XlPlacement> Werte festlegen:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>So ändern Sie das Verhalten eines Steuer Elements, sodass es sich nicht mit der Größe der Zelle ändert

1. Nennen Sie die Placement-Eigenschaft des-Steuer Elements, und legen Sie den Wert auf fest <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Weitere Informationen
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
