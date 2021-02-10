---
title: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Options Feldern
description: Erfahren Sie mehr über die Grundlagen der Verwendung von Options Feldern in einem Microsoft Excel-Arbeitsblatt, um dem Benutzer eine Möglichkeit zu verschaffen, schnell zwischen Optionen zu wechseln.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1c9da3b1d019c77988ef01e1b3c019dd3f1d775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937315"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern
  Diese exemplarische Vorgehensweise zeigt die Grundlagen der Verwendung von Options Feldern in einem Microsoft Office Excel-Arbeitsblatt, um dem Benutzer eine Möglichkeit zu verschaffen, schnell zwischen Optionen zu wechseln. In diesem Fall ändern die Optionen den Stil eines Diagramms.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Das Ergebnis als vollständiges Beispiel finden Sie im Beispiel für Excel-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen einer Gruppe von Options Feldern zu einem Arbeitsblatt.

- Ändern der Diagrammformatvorlage, wenn eine Option ausgewählt ist.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Hinzufügen eines Diagramms zu einem Arbeitsblatt
 Sie können ein Excel-Arbeitsmappenprojekt erstellen, mit dem eine vorhandene Arbeitsmappe angepasst wird. In dieser exemplarischen Vorgehensweise fügen Sie einer-Arbeitsmappe ein Diagramm hinzu und verwenden dann diese Arbeitsmappe in einer neuen Excel-Projekt Mappe. Die Datenquelle in dieser exemplarischen Vorgehensweise ist ein Arbeitsblatt mit dem Namen **Daten für das Diagramm**.

### <a name="to-add-the-data"></a>So fügen Sie die Daten hinzu

1. Öffnen Sie Microsoft Excel.

2. Klicken Sie mit der rechten Maustaste auf die Registerkarte **Tabelle3** , und klicken Sie dann im Kontextmenü auf **Umbenennen** .

3. Benennen Sie das Blatt in **Daten für das Diagramm** um.

4. Fügen Sie den **Daten für das Diagramm** die folgenden Daten hinzu, wobei Zelle A4 die linke obere Ecke ist, und die untere rechte Ecke.

   |Region/Quartal|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |Ost|600|625|675|700|
   |Nord|450|470|490|510|
   |Süd|800|750|775|790|

   Fügen Sie als nächstes dem ersten Arbeitsblatt ein Diagramm hinzu, um die Daten anzuzeigen.

### <a name="to-add-a-chart-in-excel"></a>So fügen Sie ein Diagramm in Excel hinzu

1. Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Diagramme** auf **Spalte**, und klicken Sie dann auf **alle Diagrammtypen**.

2. Klicken Sie im Dialogfeld **Diagramm einfügen** auf **OK**.

3. Klicken Sie auf der Registerkarte **Entwurf** in der Gruppe **Daten** auf **Daten auswählen**.

4. Klicken Sie im Dialogfeld **Datenquelle auswählen** auf das Feld **ChartData Range** , und deaktivieren Sie die Standardauswahl.

5. Wählen Sie im **Diagramm Blatt Daten** den Zellenblock aus, der die Zahlen enthält, die A4 in der oberen linken Ecke zu E8 in der unteren rechten Ecke enthalten.

6. Klicken Sie im Dialogfeld **Datenquelle auswählen** auf **OK**.

7. Positionieren Sie das Diagramm neu, sodass die obere rechte Ecke an der Zelle **E2** ausgerichtet ist.

8. Speichern Sie die Datei auf Laufwerk C, und benennen Sie Sie **ExcelChart.xlsx**.

9. Beenden Sie Excel.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt, das auf der **ExcelChart** -Arbeitsmappe basiert.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **mein Excel-Diagramm**. Wählen Sie im Assistenten die **Option vorhandenes Dokument kopieren** aus.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klicken Sie auf die Schaltfläche **Durchsuchen** , und navigieren Sie zu der zuvor in dieser exemplarischen Vorgehensweise erstellten Arbeitsmappe.

3. Klicken Sie auf **OK**.

     Visual Studio **öffnet die neue** Excel-Arbeitsmappe im Designer und fügt **Projektmappen-Explorer** ein.

## <a name="set-properties-of-the-chart"></a>Festlegen der Eigenschaften des Diagramms
 Wenn Sie ein neues Excel-Arbeitsmappenprojekt erstellen, in dem eine vorhandene Arbeitsmappe verwendet wird, werden die Host Steuerelemente für alle benannten Bereiche, Listen Objekte und Diagramme in der Arbeitsmappe automatisch erstellt. Sie können den Namen des Steuer Elements ändern, <xref:Microsoft.Office.Tools.Excel.Chart> indem Sie das **Eigenschaften** Fenster verwenden.

### <a name="to-change-the-name-of-the-chart-control"></a>So ändern Sie den Namen des Diagramm Steuer Elements

1. Wählen Sie <xref:Microsoft.Office.Tools.Excel.Chart> im Designer das Steuerelement aus, und ändern Sie die folgenden Eigenschaften im Fenster **Eigenschaften** .

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**datachart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Hinzufügen von Steuerelementen
 Dieses Arbeitsblatt verwendet Options Felder, um Benutzern eine Möglichkeit zu verschaffen, den Diagramm Stil schnell zu ändern. Options Felder müssen jedoch exklusiv sein – wenn eine Schaltfläche ausgewählt ist, kann keine andere Schaltfläche in der Gruppe gleichzeitig ausgewählt werden. Dieses Verhalten tritt nicht standardmäßig auf, wenn Sie einem Arbeitsblatt mehrere Options Felder hinzufügen.

 Eine Möglichkeit, dieses Verhalten hinzuzufügen, besteht darin, die Options Felder eines Benutzer Steuer Elements zu gruppieren, den Code hinter dem Benutzer Steuerelement zu schreiben und das Benutzer Steuerelement dann dem Arbeitsblatt hinzuzufügen.

### <a name="to-add-a-user-control"></a>So fügen Sie ein Benutzersteuerelement hinzu

1. Wählen Sie das **Excel-Diagramm** Projekt in **Projektmappen-Explorer** aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Benutzer Steuer** Element, benennen Sie das Steuerelement **ChartOptions,** und klicken Sie auf **Hinzufügen**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>So fügen Sie dem Benutzer Steuerelement Options Felder hinzu

1. Wenn das Benutzer Steuerelement im Designer nicht sichtbar ist, doppelklicken Sie in **Projektmappen-Explorer** auf **ChartOptions** .

2. Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der Toolbox **ein Options** Feld-Steuerelement auf das Benutzer Steuerelement, und ändern Sie die folgenden Eigenschaften. 

   | Eigenschaft | Wert |
   |----------|------------------|
   | **Name** | **columnChart** |
   | **Text** | **Säulendiagramm** |

3. Fügen Sie dem Benutzer Steuerelement ein zweites Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.

   | Eigenschaft | Wert |
   |----------|---------------|
   | **Name** | **barChart** |
   | **Text** | **Balkendiagramm** |

4. Fügen Sie dem Benutzer Steuerelement ein drittes Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.

   | Eigenschaft | Wert |
   |----------|----------------|
   | **Name** | **lineChart** |
   | **Text** | **Liniendiagramm** |

5. Fügen Sie dem Benutzer Steuerelement ein viertes Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**areaBlockChart**|
   |**Text**|**Flächendiagramm**|

   Schreiben Sie als nächstes den Code, um das Diagramm zu aktualisieren, wenn auf ein Optionsfeld geklickt wird.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Diagramm Stil bei ausgewählter Options Schaltfläche ändern
 Nun können Sie den Code hinzufügen, um den Diagramm Stil zu ändern. Erstellen Sie zu diesem Zweck ein öffentliches Ereignis für das Benutzer Steuerelement, fügen Sie eine Eigenschaft hinzu, um den Auswahltyp festzulegen, und erstellen Sie einen Ereignishandler für das- `CheckedChanged` Ereignis der einzelnen Options Felder.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>So erstellen Sie ein Ereignis und eine Eigenschaft auf einem Benutzersteuerelement

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Benutzer Steuerelement, und klicken Sie dann auf **Code anzeigen**.

2. Fügen Sie der `ChartOptions` -Klasse Code hinzu, um ein `SelectionChanged` -Ereignis und die-Eigenschaft zu erstellen `Selection` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>So behandeln Sie das CheckedChanged-Ereignis der Options Felder

1. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `areaBlockChart`-Optionsfelds fest, und erhöhen Sie dann das Ereignis.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `barChart`-Optionsfelds fest.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `columnChart`-Optionsfelds fest.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `lineChart`-Optionsfelds fest.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. In C# müssen Sie Ereignishandler für die Optionsfelder hinzufügen. Sie können den Code dem `ChartOptions`-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`. Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>Hinzufügen des Benutzer Steuer Elements zum Arbeitsblatt
 Wenn Sie die Projekt Mappe erstellen, wird das neue Benutzer Steuerelement automatisch der **Toolbox** hinzugefügt. Anschließend können Sie das Steuerelement aus der **Toolbox** in das Arbeitsblatt ziehen.

### <a name="to-add-the-user-control-your-worksheet"></a>So fügen Sie dem Benutzer Steuerelement ein Arbeitsblatt hinzu

1. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Das Benutzer Steuerelement **ChartOptions** wird der **Toolbox** hinzugefügt.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1. vb** oder **Sheet1.cs**, und klicken Sie dann auf **Designer anzeigen**.

3. Ziehen Sie das Steuerelement **ChartOptions** von der **Toolbox** auf das Arbeitsblatt.

     Dem Projekt wird ein neues Steuerelement mit dem Namen `my_Excel_Chart_ChartOptions1` hinzugefügt.

4. Ändern Sie den Namen des Steuer Elements in **ChartOptions1**.

## <a name="change-the-chart-type"></a>Ändern des Diagramm Typs
 Um den Diagrammtyp zu ändern, erstellen Sie einen Ereignishandler, der den Stil entsprechend der im Benutzer Steuerelement ausgewählten Option festlegt.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>So ändern Sie den Diagrammtyp, der im Arbeitsblatt angezeigt wird

1. Fügen Sie der Klasse `Sheet1` den folgenden Ereignishandler hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. In c# müssen Sie dem-Ereignis einen Ereignishandler für das Benutzer Steuerelement hinzufügen, <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> wie unten gezeigt. Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können Ihre Arbeitsmappe jetzt testen, um zu überprüfen, ob das Diagramm ordnungsgemäß formatiert ist, wenn Sie ein Optionsfeld auswählen.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Wählen Sie verschiedene Optionsfelder aus.

3. Stellen Sie sicher, dass sich die Diagrammformatvorlage ändert, um der Auswahl zu entsprechen.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise werden die Grundlagen der Verwendung von Options Feldern und Diagramm Stilen für Arbeitsblätter erläutert. Die folgenden Aufgaben könnten sich daran anschließen:

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

- Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Ändern Sie die Formatierung in einem Arbeitsblatt mithilfe von Kontrollkästchen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Ändern der Arbeitsblatt Formatierung mithilfe von CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)-Steuerelementen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweisen mit Excel](../vsto/walkthroughs-using-excel.md)
