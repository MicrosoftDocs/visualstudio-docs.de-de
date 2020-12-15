---
title: 'Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich'
description: Erstellen Sie einen Aktionsbereich in einem Microsoft Word-Dokument. Erfahren Sie, dass der Aktionsbereich zwei Steuerelemente enthält, die Eingaben erfassen und den Text dann an das Dokument senden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44fd876dfad99e1a1320a5e5d743ea8e30dfdb98
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524169"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein Aktionsbereich in einem Microsoft Office Word-Dokument erstellt wird. Der Aktionsbereich enthält zwei Steuerelemente, die Eingaben erfassen und dann den Text an das Dokument senden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Entwerfen Sie eine Schnittstelle mithilfe Windows Forms Steuerelemente in einem Aktionsbereich-Steuerelement.

- Zeigen Sie den Aktionsbereich an, wenn die Anwendung geöffnet wird.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Word-Dokument Projekt mit dem Namen **My Basic Actions Pane**. Wählen Sie im Assistenten **Neues Dokument erstellen** aus. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Projekt " **mein grundlegender Aktions** Bereich" hinzu.

## <a name="add-text-and-bookmarks-to-the-document"></a>Hinzufügen von Text und Lesezeichen zum Dokument
 Im Aktionsbereich wird Text an Lesezeichen im Dokument gesendet. Um das Dokument zu entwerfen, geben Sie Text ein, um ein einfaches Formular zu erstellen.

### <a name="to-add-text-to-your-document"></a>So fügen Sie dem Dokument Text hinzu

1. Geben Sie den folgenden Text in das Word-Dokument ein:

    **21. März 2008**

    **Name**

    **Adresse**

    **Dies ist ein Beispiel für einen grundlegenden Aktionsbereich in Word.**

   Sie können Ihrem Dokument ein Steuerelement hinzufügen <xref:Microsoft.Office.Tools.Word.Bookmark> , indem Sie es aus der **Toolbox** in Visual Studio ziehen oder das Dialogfeld **Lesezeichen** in Word verwenden.

### <a name="to-add-a-bookmark-control-to-your-document"></a>So fügen Sie dem Dokument ein Lesezeichen-Steuerelement hinzu

1. Ziehen Sie ein-Steuerelement auf der Registerkarte Word-Steuer **Elemente** der **Toolbox** <xref:Microsoft.Office.Tools.Word.Bookmark> auf das Dokument.

     Das Dialogfeld **Lesezeichen Steuerelement hinzufügen** wird angezeigt.

2. Wählen Sie das Wort **Name** aus, ohne die Absatz Markierung auszuwählen, und klicken Sie auf **OK**.

    > [!NOTE]
    > Die Absatz Marke sollte außerhalb des Lesezeichens liegen. Wenn Absatzmarken im Dokument nicht sichtbar sind, klicken Sie auf **das Menü** Extras, zeigen Sie auf **Microsoft Office Word-Tools** , und klicken Sie dann auf **Optionen**. Klicken Sie auf die Registerkarte **Ansicht** , und aktivieren Sie im Dialogfeld **Optionen** im Abschnitt **Formatierungs Markierungen** das Kontrollkästchen **Absatzmarken** .

3. Ändern Sie im **Eigenschaften** Fenster die **Name** -Eigenschaft von **Bookmark1 zuweisen** in **ShowName**.

4. Wählen Sie das Wort **Address** aus, ohne die Absatz Markierung auszuwählen.

5. Klicken Sie auf der Registerkarte **Einfügen** des Menübands in der Gruppe **Links** auf **Lesezeichen**.

6. Geben Sie im Dialogfeld **Lesezeichen** im Feld **Bookmark Name** den Text **Show Address** ein, und klicken Sie auf **Hinzufügen**.

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich
 Fügen Sie zum Entwerfen der Aktionsbereichs Schnittstelle dem Projekt ein Aktionsbereich-Steuerelement hinzu, und fügen Sie dann dem Aktionsbereich-Steuerelement Windows Forms-Steuerelemente hinzu.

### <a name="to-add-an-actions-pane-control"></a>So fügen Sie ein Aktionsbereich-Steuerelement hinzu

1. Wählen Sie in **Projektmappen-Explorer** das Projekt **meine grundlegenden Aktions** Bereiche aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf Aktionsbereich- **Steuer** Element, benennen Sie das Steuerelement **InsertTextControl,** und klicken Sie auf **Hinzufügen**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>So fügen Sie dem Aktionsbereich-Steuerelement Windows Form-Steuerelemente hinzu

1. Wenn das Aktionsbereich-Steuerelement im Designer nicht angezeigt wird, doppelklicken Sie auf **InsertTextControl**.

2. Ziehen Sie ein **Label** -Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement Aktionsbereich.

3. Ändern Sie die **Text** -Eigenschaft des Label-Steuer Elements in **Name**.

4. Fügen Sie dem Aktionsbereich-Steuerelement ein **TextBox** -Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**GetName**|
    |**Size**|**130, 20**|

5. Fügen Sie dem Aktionsbereich-Steuerelement ein zweites **Label** -Steuerelement hinzu, und ändern Sie die **Text** -Eigenschaft in **Address**.

6. Fügen Sie dem Aktionsbereich-Steuerelement ein zweites **TextBox** -Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**getAddress**|
    |**Akzeptiert die Rückgabe**|**Wahr**|
    |**Mehrzeilig**|**Wahr**|
    |**Size**|**130, 40**|

7. Fügen Sie dem Aktionsbereich-Steuerelement ein **Schalt** Flächen-Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**AddText**|
    |**Text**|**Einfügen**|

## <a name="add-code-to-insert-text-into-the-document"></a>Hinzufügen von Code zum Einfügen von Text in das Dokument
 Schreiben Sie im Aktionsbereich Code, der den Text aus den Textfeldern in die entsprechenden Steuer <xref:Microsoft.Office.Tools.Word.Bookmark> Elemente im Dokument einfügt. Sie können die- `Globals` Klasse verwenden, um über die Steuerelemente im Aktionsbereich auf Steuerelemente im Dokument zuzugreifen. Weitere Informationen finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>So fügen Sie Text aus dem Aktionsbereich in einem Lesezeichen im Dokument ein

1. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler der **AddText** -Schaltfläche den folgenden Code hinzu.

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. In c# müssen Sie einen Ereignishandler für den Schaltflächen Klick hinzufügen. Sie können diesen Code nach dem-Befehl im- `InsertTextControl` Konstruktor platzieren `InitializeComponent` . Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Fügen Sie Code hinzu, um den Aktionsbereich anzuzeigen.
 Fügen Sie das Steuerelement, das Sie erstellt haben, der Steuerelement Auflistung hinzu, um den Aktionsbereich anzuzeigen.

### <a name="to-show-the-actions-pane"></a>So zeigen Sie den Aktionsbereich an

1. Erstellen Sie eine neue Instanz des Aktionsbereich-Steuer Elements in der- `ThisDocument` Klasse.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. Fügen Sie dem-Ereignishandler von den folgenden Code hinzu <xref:Microsoft.Office.Tools.Word.Document.Startup> `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Testen der Anwendung
 Testen Sie das Dokument, um sicherzustellen, dass der Aktionsbereich geöffnet wird, wenn das Dokument geöffnet wird, und der Text, der in die Textfelder eingegeben wird, beim Klicken auf die Schaltfläche in die Lesezeichen eingefügt

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der Aktionsbereich angezeigt wird.

3. Geben Sie Ihren Namen und Ihre Adresse in die Textfelder im Aktionsbereich ein, und klicken Sie auf **Einfügen**.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

- Erstellen Sie einen Aktionsbereich in Excel. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Aktionsbereichs zu Excel-Arbeits](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))Mappen.

- Binden von Daten an Steuerelemente in einem Aktionsbereich. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktions](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)Bereich.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Excel-Arbeitsmappen](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Bookmark-Steuerelement](../vsto/bookmark-control.md)
