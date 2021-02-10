---
title: Ändern der Dokument Formatierung mithilfe von CheckBox-Steuerelementen
description: Erfahren Sie, wie Sie Windows Forms-Steuerelemente in einer Anpassung auf Dokument Ebene für Microsoft Word verwenden, um die Textformatierung zu ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d83fb8fad6de0c932d371f7f874cea0ff9a8f80
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958660"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der Dokument Formatierung mit CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Windows Forms Steuerelemente in einer Anpassung auf Dokument Ebene für Microsoft Office Word verwendet werden, um die Textformatierung zu ändern.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Text und einem-Steuerelement zum Dokument in einem Projekt auf Dokument Ebene zur Entwurfszeit.

- Formatieren des Texts, wenn eine Option ausgewählt ist.

  Das Ergebnis als vollständiges Beispiel finden Sie im Beispiel für Word-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="create-a-new-project"></a>Erstellen eines neuen Projekts

1. Erstellen Sie ein Word-Dokument Projekt mit dem Namen **meine Wort Formatierung**. Wählen Sie im Assistenten **Neues Dokument erstellen** aus.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Projekt " **My Word-Formatierung** " hinzu.

## <a name="add-text-and-controls-to-the-word-document"></a>Hinzufügen von Text und Steuerelementen zum Word-Dokument
 Fügen Sie in dieser exemplarischen Vorgehensweise dem Word-Dokument drei Kontrollkästchen und Text in einem-Steuerelement hinzu <xref:Microsoft.Office.Tools.Word.Bookmark> . Mit den Kontrollkästchen werden dem Benutzeroptionen zum Formatieren des Texts angezeigt.

### <a name="add-three-check-boxes"></a>Fügen Sie drei Kontrollkästchen hinzu.

1. Stellen Sie sicher, dass das Dokument im Visual Studio-Designer geöffnet ist.

2. Ziehen Sie das erste Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> auf das Dokument.

3. Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**ApplyBoldFont**|
    |**Text**|**Fett**|

4. Drücken **Sie die Eingabe** Taste, um die Einfügemarke unter das erste Kontrollkästchen zu verschieben

5. Fügen Sie dem Dokument unterhalb des Kontrollkästchens ein zweites Kontrollkästchen hinzu, `ApplyBoldFont` und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**ApplyItalicFont**|
    |**Text**|**Kursiv**|

6. Drücken **Sie die Eingabe** Taste, um die Einfügemarke unter das zweite Kontrollkästchen zu verschieben

7. Fügen Sie dem Dokument unterhalb des Kontrollkästchens ein drittes Kontrollkästchen hinzu, `ApplyItalicFont` und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyUnderlineFont**|
    |**Text**|**Underline**|

### <a name="add-text-and-a-bookmark-control"></a>Hinzufügen von Text und Lesezeichen-Steuerelementen

1. Verschieben Sie die Einfügemarke unterhalb der Kontrollkästchen-Steuerelemente, und geben Sie folgenden Text ein:

    **Aktivieren Sie das Kontrollkästchen, um die Formatierung dieses Texts zu ändern.**

2. Ziehen Sie ein-Steuerelement auf der Registerkarte Word-Steuer **Elemente** der **Toolbox** <xref:Microsoft.Office.Tools.Word.Bookmark> auf das Dokument.

    Das Dialogfeld **Lesezeichen Steuerelement hinzufügen** wird angezeigt.

3. Markieren Sie den Text, den Sie dem Dokument hinzugefügt haben, und klicken Sie auf **OK**

    <xref:Microsoft.Office.Tools.Word.Bookmark>Dem ausgewählten Text im Dokument wird ein Steuerelement mit dem Namen **Bookmark1 zuweisen** hinzugefügt.

4. Ändern Sie im Fenster **Eigenschaften** den Wert der Eigenschaft **(Name)** in **fontText.**

   Schreiben Sie als nächstes den Code, um den Text zu formatieren, wenn ein Kontrollkästchen aktiviert oder deaktiviert ist.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatieren Sie den Text, wenn ein Kontrollkästchen aktiviert oder deaktiviert ist.
 Wenn der Benutzer eine Formatierungs Option auswählt, ändern Sie das Format des Texts im Dokument.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Formatierung ändern, wenn ein Kontrollkästchen aktiviert ist

1. Klicken Sie mit der rechten Maustaste auf `ThisDocument` **Projektmappen-Explorer**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie der **ThisDocument** -Klasse nur bei c# die folgenden Konstanten hinzu.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyBoldFont` Kontrollkästchens den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyItalicFont` Kontrollkästchens den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyUnderlineFont` Kontrollkästchens den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. In c# müssen Sie dem-Ereignis Ereignishandler für die Textfelder hinzufügen <xref:Microsoft.Office.Tools.Word.Document.Startup> . Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können nun das Dokument testen, um zu überprüfen, ob der Text ordnungsgemäß formatiert ist, wenn Sie ein Kontrollkästchen aktivieren oder deaktivieren.

### <a name="test-your-document"></a>Testen des Dokuments

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Ein Kontrollkästchen aktivieren oder deaktivieren

3. Vergewissern Sie sich, dass der Text korrekt formatiert ist.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Verwendung von Kontrollkästchen und die programmgesteuerte Änderung der Textformatierung in Word-Dokumenten. Die folgenden Aufgaben könnten sich daran anschließen:

- Verwenden Sie eine Schaltfläche, um ein Textfeld aufzufüllen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Auswählen von Diagrammformaten mithilfe von Optionsfeldern. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Aktualisieren eines Diagramms in einem Dokument mithilfe](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)von Options Feldern.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
