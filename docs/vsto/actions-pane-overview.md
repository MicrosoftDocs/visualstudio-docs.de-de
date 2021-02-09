---
title: Übersicht über den Aktionsbereich
description: Erfahren Sie, wie ein Aktionsbereich ein anpassbarer Aufgabenbereich für Dokument Aktionen ist, der an ein bestimmtes Microsoft Office Word-Dokument oder eine Excel-Arbeitsmappe angefügt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9579de6712b742dde1f9b399ca8a1e4598783679
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896761"
---
# <a name="actions-pane-overview"></a>Übersicht über den Aktionsbereich
  Ein Aktionsbereich ist ein anpassbarer Aufgabenbereich für **Dokument Aktionen** , der an ein bestimmtes Microsoft Office Word-Dokument oder eine Microsoft Office Excel-Arbeitsmappe angefügt wird. Der Aktionsbereich wird im Aufgabenbereich Office zusammen mit anderen integrierten Aufgabenbereichen gehostet, wie z. b. dem Aufgabenbereich **XML-Quelle** in Excel oder dem Aufgabenbereich **Formatvorlagen und Formatierung** in Word. Sie können Windows Forms-Steuerelemente oder WPF-Steuerelemente verwenden, um die Benutzeroberfläche des Aktionsbereichs zu gestalten.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie können einen Aktionsbereich nur in einer Anpassung auf Dokumentebene für Word oder Excel erstellen. In einem VSTO-Add-In können Sie keinen Aktionsbereich erstellen. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Der Aktionsbereich unterscheidet sich von benutzerdefinierten Aufgabenbereichen. Benutzerdefinierte Aufgabenbereiche sind der Anwendung und keinem bestimmten Dokument zugeordnet. Sie können benutzerdefinierte Aufgabenbereiche in VSTO-Add-Ins für einige Microsoft Office-Anwendungen erstellen. Weitere Informationen finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

## <a name="display-the-actions-pane"></a>Anzeigen des Aktionsbereichs
 Der Aktionsbereich wird durch die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse dargestellt. Wenn Sie ein Projekt auf Dokumentebene erstellen, machen Sie eine Instanz dieser Klasse für Ihren Code verfügbar, indem Sie das `ActionsPane`-Feld der `ThisWorkbook`-Klasse (für Excel) oder der `ThisDocument`-Klasse (für Word) im Projekt verwenden. Um den Aktionsbereich anzuzeigen, fügen Sie der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>-Eigenschaft des `ActionsPane`-Felds ein Windows Forms-Steuerelement hinzu. Durch das folgende Codebeispiel wird dem Aktionsbereich ein Steuerelement namens `actions` hinzugefügt.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Der Aktionsbereich wird zur Laufzeit sichtbar, sobald Sie ihm explizit ein Steuerelement hinzufügen. Sobald der Aktionsbereich angezeigt wird, können Sie dynamisch Steuerelemente in Reaktion auf Benutzeraktionen dynamisch hinzufügen oder entfernen. Normalerweise fügen Sie den Code hinzu, um den Aktionsbereich im `Startup`-Ereignishandler von `ThisDocument` oder `ThisWorkbook` anzuzeigen, damit der Aktionsbereich sichtbar ist, wenn der Benutzer das Dokument erstmalig öffnet. Sie können den Aktionsbereich jedoch auch ausschließlich als Reaktion auf eine Benutzeraktion im Dokument anzeigen. Sie können den Code beispielsweise zum `Click`-Ereignis eines Steuerelements im Dokument hinzufügen.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Hinzufügen von mehreren Steuerelementen zum Aktionsbereich
 Wenn Sie dem Aktionsbereich mehrere Steuerelemente hinzufügen, sollten Sie die Steuerelemente in einem Benutzer Steuerelement gruppieren und dann der-Eigenschaft das Benutzer Steuerelement hinzufügen <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> . Dieser Vorgang umfasst die folgenden Schritte:

1. Erstellen Sie die Benutzeroberfläche (UI) des Aktionsbereichs, indem Sie dem Projekt ein Aktionsbereich- **Steuer** Element oder ein **Benutzer Steuer** Element hinzufügen. Beide Elemente umfassen eine benutzerdefinierte Windows Forms-<xref:System.Windows.Forms.UserControl>-Klasse. Das **Aktions** Bereich-Steuerelement und die **Benutzer Steuer** Element Elemente sind gleichwertig. der einzige Unterschied ist der Name.

2. Fügen Sie dem <xref:System.Windows.Forms.UserControl> Windows Forms-Steuerelemente durch Verwendung des Designers oder durch Schreiben von Code hinzu.

   > [!NOTE]
   > Sie können dem Aktionsbereich auch WPF-Steuerelemente hinzufügen, indem Sie dem Windows Forms-<xref:System.Windows.Forms.UserControl> ein WPF-<xref:System.Windows.Controls.UserControl> hinzufügen. Weitere Informationen finden Sie unter [Verwenden von WPF-Steuerelementen in Office](../vsto/using-wpf-controls-in-office-solutions.md)-Projektmappen.

3. Fügen Sie den im `ActionsPane`-Feld enthaltenen Steuerelementen der `ThisWorkbook`-Klasse (für Excel) oder der `ThisDocument`-Klasse (für Word) eine Instanz des benutzerdefinierten Steuerelements im Projekt hinzu.

   Beispiele zur Veranschaulichung dieses Prozesses finden Sie unter Gewusst [wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeits](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)Mappen.

## <a name="hide-the-actions-pane"></a>Bereich "Aktionen" ausblenden
 Obwohl die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse über eine <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A>-Methode und eine <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>-Eigenschaft verfügt, können Sie den Aktionsbereich nicht von der Benutzeroberfläche entfernen, indem Sie einen beliebigen Member der <xref:Microsoft.Office.Tools.ActionsPane>-Klasse selbst verwenden. Wenn die- <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> Methode aufgerufen oder die- <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Eigenschaft auf **false** festgelegt wird, werden nur die Steuerelemente im Aktionsbereich ausgeblendet. der Aufgabenbereich wird nicht ausgeblendet.

 Um den Aufgabenbereich in der Projektmappe auszublenden, haben Sie mehrere Optionen:

- Legen Sie für Word die- <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> Eigenschaft des- <xref:Microsoft.Office.Interop.Word.TaskPane> Objekts, das den Aufgabenbereich Dokument Aktionen darstellt, auf **false** fest. Das folgende Codebeispiel sollte von der `ThisDocument`-Klasse im Projekt ausgeführt werden.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Legen Sie für Excel die- <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> Eigenschaft des- <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> Objekts auf **false** fest. Das folgende Codebeispiel sollte von der `ThisWorkbook`-Klasse im Projekt ausgeführt werden.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Für Word oder Excel können Sie alternativ die- <xref:Microsoft.Office.Core.CommandBar.Visible%2A> Eigenschaft der Befehlsleiste, die den Aufgabenbereich darstellt, auf **false** festlegen. Das folgende Codebeispiel sollte von der `ThisDocument`-Klasse oder `ThisWorkbook`-Klasse im Projekt ausgeführt werden.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Löschen des Aktionsbereichs beim Öffnen des Dokuments
 Wenn ein Benutzer das Dokument speichert, während der Aktionsbereich sichtbar ist, wird der Aktionsbereich jedes Mal sichtbar, wenn das Dokument geöffnet wird, unabhängig davon, ob der Aktionsbereich Steuerelemente enthält. Wenn Sie die Anzeige steuern möchten, rufen Sie die <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A>-Methode des `ActionsPane`-Felds im `Startup`-Ereignishandler von `ThisDocument` oder `ThisWorkbook` ab, um sicherzustellen, dass der Aktionsbereich beim Öffnen des Dokuments nicht sichtbar ist.

### <a name="determine-when-the-actions-pane-is-closed"></a>Festlegen, wann der Aktionsbereich geschlossen wird
 Es gibt kein Ereignis, das beim Schließen des Aktionsbereichs ausgelöst wird. Obwohl die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse über ein <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>-Ereignis verfügt, wird dieses Ereignis nicht ausgelöst, wenn der Endbenutzer den Aktionsbereich schließt. Stattdessen wird dieses Ereignis ausgelöst, wenn die Steuerelemente im Aktionsbereich durch Aufrufen der- <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> Methode oder durch Festlegen der- <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Eigenschaft auf **false** ausgeblendet werden.

 Wenn der Benutzer den Aktionsbereich schließt, kann der Benutzer ihn erneut anzeigen, indem er eine der folgenden Prozeduren in der Benutzeroberfläche der Anwendung ausführt.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>So zeigen Sie den Aktionsbereich mithilfe der Benutzeroberfläche von Word oder Excel an

1. Klicken Sie im Menüband auf die Registerkarte **Ansicht** .

2. Klicken Sie in der Gruppe ein **-/Ausblenden** auf die UMSCHALT Fläche **Dokument Aktionen** .

## <a name="program-actions-pane-events"></a>Ereignisse im Bereich "Programm Aktionen"
 Sie können dem Aktionsbereich mehrere Benutzersteuerelemente hinzufügen und dann Code schreiben, der durch Ein- oder Ausblenden der Benutzersteuerelemente auf Ereignisse im Dokument reagiert. Wenn Sie Ihrem Dokument XML-Schemaelemente zuordnen, können Sie bestimmte Benutzersteuerelemente im Aktionsbereich einblenden, sobald sich der Einfügepunkt innerhalb eines der XML-Elemente befindet. Weitere Informationen finden Sie unter Gewusst wie: Zuordnen von [Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) und Gewusst [wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Sie können auch Code schreiben, der auf Ereignisse eines beliebigen Objekts, z. B. Hoststeuerelement-, Anwendungs- oder Dokumentereignisse, reagiert. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Program mieren gegen Ereignisse eines NamedRange-Steuer](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)Elements.

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Binden von Daten an Steuerelemente im Aktionsbereich
 Die Steuerelemente im Aktionsbereich haben die gleichen Datenbindungsfunktionen wie Steuerelemente in Windows Forms. Sie können die Steuerelemente an Datenquellen wie Datasets, typisierte Datasets und XML binden. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Sie können Steuerelemente im Aktionsbereich und Steuerelemente im Dokument an das gleiche Dataset binden. Beispielsweise können Sie eine Master-/Detailbeziehung zwischen den Steuerelementen im Aktionsbereich und den Steuerelementen im Arbeitsblatt erstellen. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktions](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)Bereich.

## <a name="validate-data-in-actions-pane-controls"></a>Überprüfen von Daten in Aktionsbereich-Steuerelementen
 Wenn Sie ein Meldungsfeld im <xref:System.Windows.Forms.Control.Validating>-Ereignishandler eines Steuerelements im Aktionsbereich anzeigen, kann das Ereignis ein zweites Mal ausgelöst werden, wenn sich der Fokus vom Steuerelement auf das Meldungsfeld verlagert. Um dies zu verhindern, verwenden Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement zum Anzeigen von Überprüfungsfehlermeldungen.

## <a name="user-control-stacking-order"></a>Stapel Reihen Reihenfolge
 Wenn Sie mehrere Benutzersteuerelemente verwenden, können Sie Code schreiben, durch den die Benutzersteuerelemente im Aktionsbereich – ob vertikal oder horizontal angedockt – richtig gestapelt werden. Sie können die Stapelreihenfolge der Benutzersteuerelemente im Aktionsbereich mithilfe der <xref:Microsoft.Office.Tools.StackStyle>-Enumeration der <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Die <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft akzeptiert die folgenden <xref:Microsoft.Office.Tools.StackStyle>-Enumerationswerte.

|Stapelstil|Definition|
|--------------------|----------------|
|FromBottom|Stapelt vom unteren Rand des Aktionsbereichs.|
|Fromleft|Stapelt vom linken Rand des Aktionsbereichs.|
|Fromright|Stapelt vom rechten Rand des Aktionsbereichs.|
|FromTop|Stapelt von oberen Rand des Aktionsbereichs.|
|Keine|Es wurde keine Stapelreihenfolge definiert; die Reihenfolge wird vom Entwickler gesteuert.|

 Im folgenden Code wird die <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft festgelegt, um die Benutzersteuerelemente vom oberen Rand des Aktionsbereichs zu stapeln.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Anker Steuerelemente
 Wenn der Benutzer die Größe des Aktionsbereichs zur Laufzeit ändert, kann sich die Größe der Steuerelemente mit dem Aktionsbereich ändern. Sie können die <xref:System.Windows.Forms.Control.Anchor%2A>-Eigenschaft eines Windows Forms-Steuerelements verwenden, um Steuerelemente im Aktionsbereich zu verankern. Auf dieselbe Weise können Sie auch die Windows Forms-Steuerelemente im Benutzersteuerelement verankern. Weitere Informationen finden Sie unter Gewusst [wie: Verankern von Steuerelementen auf Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Ändern der Größe des Aktionsbereichs
 Sie können die Größe von <xref:Microsoft.Office.Tools.ActionsPane> nicht direkt ändern, weil <xref:Microsoft.Office.Tools.ActionsPane> in den Aufgabenbereich eingebettet ist. Sie können die Breite des Aufgabenbereichs jedoch programmgesteuert ändern, indem Sie die <xref:Microsoft.Office.Core.CommandBar.Width%2A>-Eigenschaft der <xref:Microsoft.Office.Core.CommandBar> festlegen, die den Aufgabenbereich darstellt. Sie können die Höhe des Aufgabenbereichs ändern, falls er horizontal angedockt oder unverankert ist.

 Die programmgesteuerte Größenänderung des Aufgabenbereichs ist nicht empfehlenswert, da der Benutzer die Größe des Aufgabenbereichs auswählen kann, der Ihren Anforderungen am besten entspricht. Wenn Sie die Breite des Aufgabenbereichs jedoch ändern müssen, können Sie für diese Aufgabe den folgenden Code verwenden.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Neupositionieren des Aktionsbereichs
 Sie können den <xref:Microsoft.Office.Tools.ActionsPane> nicht direkt neu positionieren, da er in den Aufgabenbereich eingebettet ist. Sie können den Aufgabenbereich jedoch programmgesteuert verschieben, indem Sie die <xref:Microsoft.Office.Core.CommandBar.Position%2A>-Eigenschaft der <xref:Microsoft.Office.Core.CommandBar> festlegen, die den Aufgabenbereich darstellt.

 Das programmgesteuerte Neupositionieren des Aufgabenbereichs ist nicht empfehlenswert, da der Benutzer die Position des Aufgabenbereichs auf dem Bildschirm auswählen kann, der seinen Anforderungen am besten entspricht. Wenn Sie den Aufgabenbereich jedoch verschieben müssen, können Sie für diese Aufgabe den folgenden Code verwenden.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Endbenutzer können den Aufgabenbereich jederzeit manuell neu positionieren. Es gibt keine Möglichkeit sicherzustellen, dass der Aufgabenbereich an der Position angedockt bleibt, die Sie programmgesteuert festlegen. Allerdings können Sie Änderungen in Bezug auf die Ausrichtung suchen und sicherstellen, dass die Steuerelemente im Aktionsbereich in der richtigen Richtung gestapelt sind. Weitere Informationen finden Sie unter Gewusst [wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Das Festlegen der <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> -Eigenschaft und der-Eigenschaft <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> des <xref:Microsoft.Office.Tools.ActionsPane> ändert seine Position nicht, da das- <xref:Microsoft.Office.Tools.ActionsPane> Objekt in den Aufgabenbereich eingebettet ist.

 Wenn der Aufgabenbereich nicht angedockt ist, können Sie die <xref:Microsoft.Office.Core.CommandBar.Top%2A>-Eigenschaft und die <xref:Microsoft.Office.Core.CommandBar.Left%2A>-Eigenschaft von <xref:Microsoft.Office.Core.CommandBar> festlegen, der den Aufgabenbereich darstellt. Durch den folgenden Code wird ein nicht angedockter Aufgabenbereich in die obere linke Ecke des Dokuments verschoben.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Weitere Informationen
- [Verwenden von WPF-Steuerelementen in Office-Lösungen](../vsto/using-wpf-controls-in-office-solutions.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
