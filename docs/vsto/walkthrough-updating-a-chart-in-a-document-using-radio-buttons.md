---
title: 'Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Options Feldern'
description: Erfahren Sie, wie Sie Options Felder in einer Anpassung auf Dokument Ebene für Microsoft Word verwenden können, um Benutzern die Auswahl von Diagramm Stilen für das Dokument zu gestatten.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0db8cd113983231ee45252fec8fb47e3a7b75b7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937328"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Options Feldern
  Diese Vorgehensweise zeigt Ihnen, wie Sie Optionsfelder in einer Anpassung auf Dokumentebene für Microsoft Office Word verwenden, um Benutzern die Möglichkeit zu geben, Diagrammformatvorlagen im Dokument auszuwählen.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen eines Diagramms zum Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.

- Gruppieren von Optionsfeldern durch Hinzufügen zu einem Benutzersteuerelement.

- Ändern der Diagrammformatvorlage, wenn eine Option ausgewählt ist.

  Das Ergebnis als vollständiges Beispiel finden Sie im Beispiel für Word-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Word-Dokument Projekt mit dem Namen **meine Diagramm Optionen**. Wählen Sie im Assistenten **Neues Dokument erstellen** aus. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Projekt " **meine Diagramm Optionen** " hinzu.

## <a name="add-a-chart-to-the-document"></a>Hinzufügen eines Diagramms zum Dokument

### <a name="to-add-a-chart"></a>So fügen Sie ein Diagramm hinzu

1. Klicken Sie im Word-Dokument, das im Visual Studio-Designer gehostet wird, auf dem Menüband auf die Registerkarte **Einfügen** .

2. Klicken Sie in der Gruppe **Text** auf die Dropdown-Schaltfläche **Objekt einfügen** und dann auf **Objekt**.

     Das Dialogfeld **Objekt** wird geöffnet.

3. Wählen Sie in der Liste **Objekttyp** auf der Registerkarte **neu erstellen** **Microsoft Graph Diagramm** aus, und klicken Sie dann auf **OK**.

     Ein Diagramm wird dem Dokument an der Einfügemarke hinzugefügt, und das **Daten** Blatt Fenster wird mit einigen Standarddaten angezeigt.

4. Schließen Sie das **Daten** Blatt Fenster, um die Standardwerte im Diagramm zu akzeptieren, und klicken Sie in das Dokument, um den Fokus vom Diagramm zu entfernen.

5. Klicken Sie mit der rechten Maustaste auf das Diagramm, und klicken Sie auf **Objekt formatieren**.

6. Wählen Sie im Dialogfeld **Objekt formatieren** auf der Registerkarte **Layout** die Option **Square** aus, und klicken Sie auf **OK**.

## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt
 Optionsfelder in einem Dokument schließen sich standardmäßig nicht gegenseitig aus. Sie können dafür sorgen, dass sie ordnungsgemäß funktionieren, indem Sie sie einem Benutzersteuerelement hinzufügen und dann Code schreiben, um die Auswahl zu steuern.

### <a name="to-add-a-user-control"></a>So fügen Sie ein Benutzersteuerelement hinzu

1. Wählen Sie in **Projektmappen-Explorer** das Projekt **meine Diagramm Optionen** aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Benutzer Steuer** Element, benennen Sie das Steuerelement **ChartOptions,** und klicken Sie auf **Hinzufügen**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>So fügen Sie dem Benutzersteuerelement Windows Forms-Steuerelemente hinzu

1. Wenn das Benutzer Steuerelement im Designer nicht sichtbar ist, doppelklicken Sie in **Projektmappen-Explorer** auf **ChartOptions** .

2. Ziehen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** das  erste Optionsfeld-Steuerelement auf das Benutzer Steuerelement, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**columnChart**|
    |**Text**|**Säulendiagramm**|

3. Fügen Sie dem Benutzer Steuerelement **ein zweites Options** Feld hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**barChart**|
    |**Text**|**Balkendiagramm**|

4. Fügen Sie dem Benutzer Steuerelement **ein drittes Options** Feld hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**lineChart**|
    |**Text**|**Liniendiagramm**|

5. Fügen Sie dem Benutzer Steuerelement **ein viertes Options** Feld hinzu, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**areaBlockChart**|
    |**Text**|**Flächendiagramm**|

## <a name="add-references"></a>Hinzufügen von Verweisen
 Um über das Benutzer Steuerelement in einem Dokument auf das Diagramm zuzugreifen, benötigen Sie einen Verweis auf die- `Microsoft.Office.Interop.Graph` Assembly in Ihrem Projekt.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>So fügen Sie einen Verweis auf die Microsoft.Office.Interop.Graph-Assembly hinzu

1. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.

     Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

2. Wählen Sie auf der Registerkarte **.net** die Option **Microsoft. Office. Interop. Graph** aus, und klicken Sie auf **OK**. Verwenden Sie die 14.0.0.0-Version der Assembly.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Diagramm Stil bei ausgewählter Options Schaltfläche ändern
 Damit die Schaltflächen ordnungsgemäß funktionieren, erstellen Sie ein öffentliches Ereignis auf dem Benutzersteuerelement, fügen Sie eine Eigenschaft hinzu, um den Auswahltyp festzulegen, und erstellen Sie eine Prozedur für das `CheckedChanged`-Ereignis der einzelnen Optionsfelder.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>So erstellen Sie ein Ereignis und eine Eigenschaft auf einem Benutzersteuerelement

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Benutzer Steuerelement, und klicken Sie dann auf **Code anzeigen**.

2. Fügen Sie Code hinzu, um ein `SelectionChanged`-Ereignis und die `Selection`-Eigenschaft der `ChartOptions`-Klasse zu erstellen.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>So behandeln Sie das CheckedChange-Ereignis der Optionsfelder

1. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `areaBlockChart`-Optionsfelds fest, und erhöhen Sie dann das Ereignis.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `barChart`-Optionsfelds fest.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `columnChart`-Optionsfelds fest.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. Legen Sie den Diagrammtyp im `CheckedChanged`-Ereignishandler des `lineChart`-Optionsfelds fest.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. In C# müssen Sie Ereignishandler für die Optionsfelder hinzufügen. Sie können den Code dem `ChartOptions`-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Hinzufügen des Benutzer Steuer Elements zum Dokument
 Wenn Sie die Projekt Mappe erstellen, wird das neue Benutzer Steuerelement automatisch der **Toolbox** hinzugefügt. Anschließend können Sie das Steuerelement aus der **Toolbox** in das Dokument ziehen.

### <a name="to-add-the-user-control-your-document"></a>So fügen Sie dem Dokument das Benutzersteuerelement hinzu

1. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Das Benutzer Steuerelement **ChartOptions** wird der **Toolbox** hinzugefügt.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument. vb** oder **ThisDocument.cs**, und klicken Sie dann auf **Designer anzeigen**.

3. Ziehen `ChartOptions` Sie das Steuerelement aus der **Toolbox** in das Dokument.

     Benennen Sie das Steuerelement, das Sie soeben dem Dokument hinzugefügt haben, im Fenster **Eigenschaften**  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Ändern des Diagramm Typs
 Erstellen Sie einen Ereignishandler, um den Diagrammtyp gemäß der im Benutzersteuerelement ausgewählten Option zu ändern.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>So ändern Sie den Diagrammtyp, der im Dokument angezeigt wird

1. Fügen Sie der Klasse `ThisDocument` den folgenden Ereignishandler hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. In C# müssen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>-Ereignis einen Ereignishandler für das Benutzersteuerelement hinzufügen.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können jetzt Ihr Dokument testen, um sicherzustellen, dass die Diagrammformatvorlage ordnungsgemäß aktualisiert wird, wenn Sie ein Optionsfeld auswählen.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Wählen Sie verschiedene Optionsfelder aus.

3. Stellen Sie sicher, dass sich die Diagrammformatvorlage ändert, um der Auswahl zu entsprechen.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

- Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Ändern der Formatierung durch Auswahl eines Formats aus einem Kombinationsfeld. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Ändern der Dokument Formatierung mithilfe von CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)-Steuerelementen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
