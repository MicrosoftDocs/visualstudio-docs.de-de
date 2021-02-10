---
title: Ändern der Arbeitsblatt Formatierung mithilfe von CheckBox-Steuerelementen
description: Erfahren Sie, wie Sie Office-Entwicklungs Tools in Visual Studio verwenden können, um Code zu erstellen und zu Ihrem Projekt hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 908660693abce2f2adf07d98e7f2a451a8f3c8e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956593"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der Arbeitsblatt Formatierung mit CheckBox-Steuerelementen
  Diese exemplarische Vorgehensweise zeigt die Grundlagen der Verwendung von Kontrollkästchen in einem Microsoft Office Excel-Arbeitsblatt, um die Formatierung zu ändern. Sie verwenden die Office-Entwicklungs Tools in Visual Studio, um Code zu erstellen und zu Ihrem Projekt hinzuzufügen. Das Ergebnis als vollständiges Beispiel finden Sie im Beispiel für Excel-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Hinzufügen von Text und Steuerelementen zu einem Arbeitsblatt.

- Formatiert den Text, wenn eine Option ausgewählt ist.

- Testen Sie das Projekt.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt mithilfe von Visual Studio.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **Meine Excel-Formatierung**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt das Projekt **My Excel** -Formatierung **Projektmappen-Explorer** hinzu.

## <a name="add-text-and-controls-to-the-worksheet"></a>Hinzufügen von Text und Steuerelementen zum Arbeitsblatt
 In dieser exemplarischen Vorgehensweise benötigen Sie drei <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> Steuerelemente und Text in einem- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement.

### <a name="to-add-three-check-boxes"></a>So fügen Sie drei Kontrollkästchen hinzu

1. Vergewissern Sie sich, dass die Arbeitsmappe im Visual Studio-Designer geöffnet ist und `Sheet1` geöffnet ist.

2. Ziehen Sie ein-Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> auf oder in der Nähe von Zelle **B2** in **Sheet1**.

3. Wählen Sie im Menü **Ansicht** die Option **Eigenschaften** Fenster aus.

4. Stellen Sie sicher, dass **CheckBox1** im Listenfeld Objektname des **Eigenschaften** Fensters sichtbar ist, und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**ApplyBoldFont**|
    |**Text**|**Fett**|

5. Ziehen Sie ein zweites Kontrollkästchen auf oder in der Nähe von Zelle **B4** , und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**ApplyItalicFont**|
    |**Text**|**Kursiv**|

6. Ziehen Sie ein drittes Kontrollkästchen auf oder in der Nähe von Zelle **B6** , und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyUnderlineFont**|
    |**Text**|**Underline**|

7. Aktivieren Sie alle drei Kontrollkästchen-Steuerelemente, während die **STRG** -Taste gedrückt wird.

8. Klicken Sie in Excel in der Gruppe Anordnen der Registerkarte Format auf **Ausrichten**, und klicken Sie dann auf **Links ausrichten**.

     Die drei Kontrollkästchen-Steuerelemente werden auf der linken Seite an der Position des ersten Steuer Elements ausgerichtet, das Sie ausgewählt haben.

     Als nächstes ziehen Sie ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf das Arbeitsblatt.

    > [!NOTE]
    > Sie können das Steuerelement auch hinzufügen, <xref:Microsoft.Office.Tools.Excel.NamedRange> indem Sie **Textfont** in das Feld **Name** eingeben.

#### <a name="to-add-text-to-a-namedrange-control"></a>So fügen Sie einem Name Drange-Steuerelement Text hinzu

1. Ziehen Sie ein-Steuerelement auf der Registerkarte Excel-Steuer **Elemente** der Toolbox <xref:Microsoft.Office.Tools.Excel.NamedRange> auf Zelle **B9**.

2. Vergewissern Sie sich, dass **$B $9** im bearbeitbaren Textfeld angezeigt wird und dass Zelle **B9** ausgewählt ist. Wenn dies nicht der Fall ist, klicken Sie auf Zelle **B9** , um Sie auszuwählen.

3. Klicken Sie auf **OK**.

4. Zelle **B9** wird zu einem Bereich mit dem Namen `NamedRange1` .

    Es gibt keinen sichtbaren Hinweis auf das Arbeitsblatt, wird jedoch `NamedRange1` im **Feld Name** (direkt oberhalb des Arbeitsblatts auf der linken Seite) angezeigt, wenn Cell **B9** ausgewählt ist.

5. Stellen Sie sicher, dass **NamedRange1** im Listenfeld Objektname des **Eigenschaften** Fensters sichtbar ist, und ändern Sie die folgenden Eigenschaften:

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**Textfont**|
   |**Value2**|**Aktivieren Sie das Kontrollkästchen, um die Formatierung dieses Texts zu ändern.**|

   Schreiben Sie als nächstes den Code, um den Text zu formatieren, wenn eine Option ausgewählt ist.

## <a name="format-the-text-when-an-option-is-selected"></a>Formatieren Sie den Text, wenn eine Option ausgewählt ist.
 In diesem Abschnitt schreiben Sie Code, damit das Format des Texts im Arbeitsblatt geändert wird, wenn der Benutzer eine Formatierungs Option auswählt.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>So ändern Sie die Formatierung, wenn ein Kontrollkästchen aktiviert ist

1. Klicken Sie mit der rechten Maustaste auf **Sheet1**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyBoldFont` Kontrollkästchens den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyItalicFont` Kontrollkästchens den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler des `applyUnderlineFont` Kontrollkästchens den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. In c# müssen Sie dem- <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten gezeigt Ereignishandler für die Kontrollkästchen hinzufügen. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können Ihre Arbeitsmappe jetzt testen, um sicherzustellen, dass der Text ordnungsgemäß formatiert ist, wenn Sie ein Kontrollkästchen aktivieren oder deaktivieren.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Ein Kontrollkästchen aktivieren oder deaktivieren

3. Vergewissern Sie sich, dass der Text korrekt formatiert ist.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Verwendung von Kontrollkästchen und Formatieren von Text in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweisen mit Excel](../vsto/walkthroughs-using-excel.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
