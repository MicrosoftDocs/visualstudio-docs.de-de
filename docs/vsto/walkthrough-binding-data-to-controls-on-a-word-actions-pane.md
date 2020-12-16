---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich'
description: Binden von Daten an Steuerelemente in einem Aktionsbereich in Microsoft Word. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76dffda9b332b9b76d6c0e0a423073959bcc7a56
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526206"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich
  In dieser exemplarischen Vorgehensweise wird die Datenbindung an Steuerelemente in einem Aktionsbereich in Word veranschaulicht. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Aktionsbereichs mit Windows Forms-Steuerelementen, die an Daten gebunden sind.

- Verwenden einer Master-/Detail-Beziehung zum Anzeigen von Daten in den-Steuerelementen.

- Zeigen Sie den Aktionsbereich an, wenn die Anwendung geöffnet wird.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind SQL Server.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-the-project"></a>Erstellen des Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Word-Dokument Projekt mit dem Namen **Aktions** Bereich. Wählen Sie im Assistenten **Neues Dokument erstellen** aus.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Projekt " **mein Word-Aktions** Bereich" hinzu.

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich
 In dieser exemplarischen Vorgehensweise benötigen Sie ein Aktionsbereich-Steuerelement, das Daten gebundene Windows Forms Steuerelemente enthält. Fügen Sie dem Projekt eine Datenquelle hinzu, und ziehen Sie dann die Steuerelemente aus dem Fenster **Datenquellen** in das Steuerelement Aktionsbereich.

### <a name="to-add-an-actions-pane-control"></a>So fügen Sie ein Aktionsbereich-Steuerelement hinzu

1. Wählen Sie in **Projektmappen-Explorer** das Projekt " **mein Word-Aktions** Bereich" aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Aktionsbereich- **Steuer** Element aus, benennen Sie es mit " **aktionscontrol**", **und klicken Sie** dann auf

### <a name="to-add-a-data-source-to-the-project"></a>So fügen Sie dem Projekt eine Datenquelle hinzu

1. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

   > [!NOTE]
   > Wenn **Datenquellen anzeigen** nicht verfügbar ist, klicken Sie auf das Word-Dokument, und wiederholen Sie dann den Vorgang.

2. Klicken Sie zum Starten des **Assistenten zum Konfigurieren von Datenquellen** auf **neue Datenquelle hinzufügen** .

3. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind SQL Server aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Klicken Sie auf **Weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn Sie ausgewählt ist, und klicken Sie dann auf **weiter**.

7. Erweitern Sie den Knoten **Tabellen** im Fenster **Datenbankobjekte** .

8. Aktivieren Sie das Kontrollkästchen neben den Tabellen **Suppliers** und **Products** .

9. Klicken Sie auf **Fertig stellen**.

   Der Assistent fügt dem **Datenquellen** Fenster die Tabelle " **Suppliers** " und die Tabelle " **Products** " hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer** sichtbar ist.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement Daten gebundene Windows Forms Steuerelemente hinzu

1. Erweitern Sie im **Datenquellen** Fenster die Tabelle **Suppliers** .

2. Klicken Sie auf den Dropdown Pfeil im Knoten **Firmen Name** , und wählen Sie **ComboBox** aus.

3. Ziehen Sie **CompanyName** aus dem **Datenquellen** Fenster in das Aktionsbereich-Steuerelement.

     Ein- <xref:System.Windows.Forms.ComboBox> Steuerelement wird im Aktionsbereich-Steuerelement erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden ein benannter `SuppliersBindingSource` , ein Tabellen Adapter und ein <xref:System.Data.DataSet> dem Projekt in der Komponenten Leiste hinzugefügt.

4. Wählen Sie `SuppliersBindingNavigator` in der **Komponenten** Leiste aus , und drücken Sie ENTF. In dieser exemplarischen Vorgehensweise wird das nicht verwendet `SuppliersBindingNavigator` .

    > [!NOTE]
    > Beim Löschen `SuppliersBindingNavigator` von wird nicht der gesamte Code entfernt, der für ihn generiert wurde. Sie können diesen Code entfernen.

5. Verschieben Sie das Kombinations Feld, sodass es sich unter der Bezeichnung befindet, und ändern Sie die **size** -Eigenschaft in **171, 21**.

6. Erweitern Sie im **Datenquellen** Fenster die **Products** -Tabelle, die der **Suppliers** -Tabelle untergeordnet ist.

7. Klicken Sie auf den Dropdown Pfeil auf dem Knoten **ProductName** , und wählen Sie **ListBox** aus.

8. Ziehen Sie **ProductName** in das Aktionsbereich-Steuerelement.

     Ein- <xref:System.Windows.Forms.ListBox> Steuerelement wird im Aktionsbereich-Steuerelement erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` werden dem Projekt in der Komponenten Leiste ein benannter und ein Tabellen Adapter hinzugefügt.

9. Verschieben Sie das Listenfeld so, dass es sich unter der Bezeichnung befindet, und ändern Sie die **size** -Eigenschaft in **171, 95**.

10. Ziehen <xref:System.Windows.Forms.Button> Sie ein aus der **Toolbox** auf das Aktionsbereich-Steuerelement, und platzieren Sie es unter dem Listenfeld.

11. Klicken Sie mit der rechten Maustaste <xref:System.Windows.Forms.Button> auf, klicken Sie im Kontextmenü auf **Eigenschaften** , und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**Einfügen**|
    |**Text**|**Einfügen**|

12. Passen Sie die Größe des Benutzer Steuer Elements an die Steuerelemente an.

## <a name="set-up-the-data-source"></a>Einrichten der Datenquelle
 Fügen Sie zum Einrichten der Datenquelle dem <xref:System.Windows.Forms.UserControl.Load> -Ereignis des Aktionsbereich-Steuer Elements Code hinzu, um das-Steuerelement mit Daten aus dem zu füllen <xref:System.Data.DataTable> , und legen Sie <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> für jedes Steuerelement die-Eigenschaft und die-Eigenschaft fest

### <a name="to-load-the-control-with-data"></a>So laden Sie das Steuerelement mit Daten

1. <xref:System.Windows.Forms.UserControl.Load>Fügen Sie im-Ereignishandler der- `ActionsControl` Klasse den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. In c# müssen Sie den-Ereignishandler an das- <xref:System.Windows.Forms.UserControl.Load> Ereignis anfügen. Sie können diesen Code nach dem-Befehl im- `ActionsControl` Konstruktor platzieren `InitializeComponent` . Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>So legen Sie die Daten Bindungseigenschaften der Steuerelemente fest

1. Wählen Sie das `CompanyNameComboBox`-Steuerelement.

2. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche rechts neben der **DataSource** -Eigenschaft, und wählen Sie **SuppliersBindingSource** aus.

3. Klicken Sie rechts neben der **DisplayMember** -Eigenschaft auf die Schaltfläche, und wählen Sie **CompanyName** aus.

4. Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **Text** -Eigenschaft, und wählen Sie **keine** aus.

5. Wählen Sie das `ProductNameListBox`-Steuerelement.

6. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche rechts neben der **DataSource** -Eigenschaft, und wählen Sie **ProductBindingSource** aus.

7. Klicken Sie rechts neben der **DisplayMember** -Eigenschaft auf die Schaltfläche, und wählen Sie **ProductName** aus.

8. Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **SelectedValue** -Eigenschaft, und wählen Sie **keine** aus.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Hinzufügen einer Methode zum Einfügen von Daten in eine Tabelle
 Die nächste Aufgabe besteht darin, die Daten aus den gebundenen Steuerelementen zu lesen und eine Tabelle in Ihrem Word-Dokument aufzufüllen. Erstellen Sie zunächst eine Prozedur zum Formatieren der Überschriften in der Tabelle, und fügen Sie dann die `AddData` -Methode zum Erstellen und Formatieren einer Word-Tabelle hinzu.

### <a name="to-format-the-table-headings"></a>So formatieren Sie die Tabellen Überschriften

1. Erstellen Sie in der- `ActionsControl` Klasse eine-Methode, um die Überschriften der Tabelle zu formatieren.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>So erstellen Sie die Tabelle

1. `ActionsControl`Schreiben Sie in der-Klasse eine Methode, die eine Tabelle erstellt, wenn Sie noch nicht vorhanden ist, und fügen Sie der Tabelle Daten aus dem Aktionsbereich hinzu.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>So fügen Sie Text in eine Word-Tabelle ein

1. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler der Schaltfläche " **Einfügen** " den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. In c# müssen Sie einen Ereignishandler für das- <xref:System.Windows.Forms.Control.Click> Ereignis der Schaltfläche erstellen.  Sie können diesen Code im- <xref:System.Windows.Forms.UserControl.Load> Ereignishandler der- `ActionsControl` Klasse platzieren.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Aktionsbereich anzeigen
 Der Aktionsbereich wird nach dem Hinzufügen von Steuerelementen sichtbar.

### <a name="to-show-the-actions-pane"></a>So zeigen Sie den Aktionsbereich an

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument. vb** oder **ThisDocument.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Erstellen Sie eine neue Instanz des Steuer Elements am Anfang der `ThisDocument` Klasse, damit Sie wie im folgenden Beispiel aussieht.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Fügen Sie dem- <xref:Microsoft.Office.Tools.Word.Document.Startup> Ereignishandler von Code hinzu `ThisDocument` , sodass er wie im folgenden Beispiel aussieht.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie Ihr Dokument testen, um zu überprüfen, ob der Aktionsbereich beim Öffnen des Dokuments angezeigt wird. Testen Sie die Master/Detail-Beziehung in den Steuerelementen im Aktionsbereich, und stellen Sie sicher, dass Daten in einer Word-Tabelle aufgefüllt werden, wenn auf die Schaltfläche **Einfügen** geklickt wird.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der Aktionsbereich angezeigt wird.

3. Wählen Sie im Kombinations Feld ein Unternehmen aus, und überprüfen Sie, ob die Elemente im Listenfeld **Produkte** geändert werden.

4. Wählen Sie ein Produkt aus, klicken Sie im Aktionsbereich auf **Einfügen** , und überprüfen Sie, ob die Produktdetails der Tabelle in Word hinzugefügt werden.

5. Fügen Sie zusätzliche Produkte aus verschiedenen Unternehmen ein.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Bindung von Daten an Steuerelemente in einem Aktionsbereich in Word. Die folgenden Aufgaben könnten sich daran anschließen:

- Binden von Daten an Steuerelemente in Excel. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktions](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)Bereich.

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
