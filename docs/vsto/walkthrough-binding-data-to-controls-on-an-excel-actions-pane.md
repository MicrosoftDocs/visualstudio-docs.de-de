---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich'
description: Binden von Daten an Steuerelemente in einem Aktionsbereich in Microsoft Excel. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.
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
ms.openlocfilehash: 6c53f4c1dfe9838fe4522dcc71b675a7f6b868d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524975"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht die Datenbindung an Steuerelemente in einem Aktionsbereich in Microsoft Office Excel. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Steuerelementen zu einem Arbeitsblatt

- Erstellen eines Aktionsbereich-Steuer Elements.

- Hinzufügen von Daten gebundenen Windows Forms-Steuerelementen zu einem Aktionsbereich-Steuerelement.

- Hiermit wird der Aktionsbereich angezeigt, wenn die Anwendung geöffnet wird.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind SQL Server.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-the-project"></a>Erstellen des Projekts
 Zunächst müssen Sie ein Excel-Arbeitsmappenprojekt erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen " **Meine Excel-Aktionen**". Wählen Sie im Assistenten **Neues Dokument erstellen** aus. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt **Projektmappen-Explorer** das Projekt **Meine Excel-Aktions** Bereiche hinzu.

## <a name="add-a-new-data-source-to-the-project"></a>Fügen Sie dem Projekt eine neue Datenquelle hinzu.

### <a name="to-add-a-new-data-source-to-the-project"></a>So fügen Sie dem Projekt eine neue Datenquelle hinzu

1. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind SQL Server aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Klicken Sie auf **Weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn Sie ausgewählt ist, und klicken Sie dann auf **weiter**.

7. Erweitern Sie den Knoten **Tabellen** im Fenster **Datenbankobjekte** .

8. Aktivieren Sie das Kontrollkästchen neben der Tabelle **Suppliers** .

9. Erweitern Sie die Tabelle **Products** , und wählen Sie **ProductName**, **SupplierID**, **QuantityPerUnit** und **UnitPrice** aus.

10. Klicken Sie auf **Fertig stellen**.

    Der Assistent fügt dem **Datenquellen** Fenster die Tabelle " **Suppliers** " und die Tabelle " **Products** " hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer** sichtbar ist.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 Fügen Sie als nächstes <xref:Microsoft.Office.Tools.Excel.NamedRange> dem ersten Arbeitsblatt ein-Steuerelement und ein-Steuerelement hinzu <xref:Microsoft.Office.Tools.Excel.ListObject> .

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>So fügen Sie ein Name Drange-Steuerelement und ein ListObject-Steuerelement hinzu

1. Vergewissern Sie sich, dass die **Meine Excel-Aktionen Pane.xlsx** Arbeitsmappe im Visual Studio-Designer geöffnet ist, wobei `Sheet1` angezeigt wird.

2. Erweitern Sie im **Datenquellen** Fenster die Tabelle **Suppliers** .

3. Klicken Sie auf den Dropdown Pfeil im Knoten **Firmen Name** , und klicken Sie dann auf **NamedRange**.

4. Ziehen Sie **Company Name** aus dem **Datenquellen** Fenster in die Zelle **a2** in `Sheet1` .

     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement `CompanyNameNamedRange` mit dem Namen wird erstellt, und der Text wird \<CompanyName> in Zelle **a2** angezeigt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden dem Projekt ein benannter `suppliersBindingSource` , ein Tabellen Adapter und ein <xref:System.Data.DataSet> hinzugefügt. Das-Steuerelement ist an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> , das wiederum an die-Instanz gebunden ist <xref:System.Data.DataSet> .

5. Scrollen Sie im Fenster **Datenquellen** nach unten zu den Spalten, die sich in der Tabelle **Suppliers** befinden. Am Ende der Liste befindet sich die Tabelle " **Products** ". Dies liegt daran, dass es sich um ein untergeordnetes Element der **Suppliers** -Tabelle handelt. Wählen Sie diese **Products** -Tabelle aus, nicht die, die sich auf derselben Ebene wie die **Suppliers** -Tabelle befindet, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

6. Klicken Sie in der Dropdown Liste auf **ListObject** , und ziehen Sie dann die Tabelle **Products** in die Zelle **a6** in `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject> `ProductNameListObject` In der Zelle **a6** wird ein Steuerelement mit dem Namen erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden dem Projekt ein benannter `productsBindingSource` und ein Tabellen Adapter hinzugefügt. Das-Steuerelement ist an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> , das wiederum an die-Instanz gebunden ist <xref:System.Data.DataSet> .

7. Wählen Sie für c# nur **SuppliersBindingSource** auf der Komponenten Leiste aus, und ändern Sie im **Eigenschaften** Fenster die Eigenschaft **modifiers** in **intern** .

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich
 Als nächstes benötigen Sie ein Aktionsbereich-Steuerelement mit einem Kombinations Feld.

### <a name="to-add-an-actions-pane-control"></a>So fügen Sie ein Aktionsbereich-Steuerelement hinzu

1. Wählen Sie in **Projektmappen-Explorer** das Projekt **Meine Excel-Aktions** Bereiche aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Aktionsbereich- **Steuer** Element aus, benennen Sie es mit " **aktionscontrol**", **und klicken Sie** auf

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement Daten gebundene Windows Forms Steuerelemente hinzu

1. Ziehen Sie ein-Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** <xref:System.Windows.Forms.ComboBox> auf das Steuerelement Aktionsbereich.

2. Ändern Sie die **size** -Eigenschaft in **171, 21**.

3. Passen Sie die Größe des Benutzer Steuer Elements an das Kombinations Feld an.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Binden des Steuer Elements im Aktionsbereich an Daten
 In diesem Abschnitt legen Sie die Datenquelle von <xref:System.Windows.Forms.ComboBox> auf die gleiche Datenquelle fest wie das- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf dem Arbeitsblatt.

### <a name="to-set-data-binding-properties-of-the-control"></a>So legen Sie Daten Bindungseigenschaften für das Steuerelement fest

1. Klicken Sie mit der rechten Maustaste auf das Steuerelement Aktionsbereich, und klicken Sie dann auf **Code anzeigen**

2. Fügen Sie dem-Ereignis des Aktionsbereich-Steuer Elements den folgenden Code hinzu <xref:System.Windows.Forms.UserControl.Load> .

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. In c# müssen Sie einen Ereignishandler für den erstellen `ActionsControl` . Sie können diesen Code im `ActionsControl` Konstruktor platzieren. Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Aktionsbereich anzeigen
 Der Aktionsbereich ist erst sichtbar, wenn Sie das Steuerelement zur Laufzeit hinzufügen.

#### <a name="to-show-the-actions-pane"></a>So zeigen Sie den Aktionsbereich an

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *ThisWorkbook. vb* oder *ThisWorkbook.cs*, und klicken Sie dann auf **Code anzeigen**.

2. Erstellen Sie eine neue Instanz des Benutzer Steuer Elements in der- `ThisWorkbook` Klasse.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>Fügen Sie im-Ereignishandler von `ThisWorkbook` dem Aktionsbereich das-Steuerelement hinzu.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie Ihr Dokument testen, um zu überprüfen, ob der Aktionsbereich geöffnet wird, wenn das Dokument geöffnet wird, und dass die Steuerelemente eine Master-/Detail-Beziehung aufweisen.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der Aktionsbereich angezeigt wird.

3. Wählen Sie im Listenfeld ein Unternehmen aus. Vergewissern Sie sich, dass der Name des Unternehmens im-Steuerelement aufgeführt ist <xref:Microsoft.Office.Tools.Excel.NamedRange> und die Produktdetails im-Steuerelement aufgelistet sind <xref:Microsoft.Office.Tools.Excel.ListObject> .

4. Wählen Sie verschiedene Unternehmen aus, um die Änderung von Firmenname und Produktdetails nach Bedarf zu überprüfen.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

- Binden von Daten an Steuerelemente in Word. Weitere Informationen finden Sie unter Exemplarische [Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktions](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)Bereich.

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
