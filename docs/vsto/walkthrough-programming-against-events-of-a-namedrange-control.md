---
title: 'Exemplarische Vorgehensweise: Program mieren gegen Ereignisse eines NamedRange-Steuer Elements'
description: Erfahren Sie, wie Sie einem Microsoft Excel-Arbeitsblatt ein Name Drange-Steuerelement hinzufügen und es mit den Office-Entwicklungs Tools in Visual Studio für seine Ereignisse programmieren können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e311a567d32ee083bcc13f417c248f5f3d3ee5a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526126"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Exemplarische Vorgehensweise: Program mieren gegen Ereignisse eines NamedRange-Steuer Elements
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement mithilfe von Office-Entwicklungs Tools in Visual Studio zu einem Microsoft Office Excel-Arbeitsblatt hinzugefügt und für seine Ereignisse verwendet wird.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Fügen Sie einem Arbeitsblatt ein-Steuerelement hinzu <xref:Microsoft.Office.Tools.Excel.NamedRange> .

- Programm für <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement Ereignisse.

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

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **benannte Bereichs Ereignisse**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt **Projektmappen-Explorer** das Projekt für **benannte Bereichs Ereignisse** hinzu.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Hinzufügen von Text und benannten Bereichen zum Arbeitsblatt
 Da Host Steuerelemente erweiterte Office-Objekte sind, können Sie Sie dem Dokument auf die gleiche Weise hinzufügen wie das Native Objekt. Beispielsweise können Sie einem Arbeitsblatt ein Excel-Steuerelement hinzufügen <xref:Microsoft.Office.Tools.Excel.NamedRange> , indem Sie das Menü **Einfügen** öffnen, auf **Name** zeigen und dann **definieren** auswählen. Sie können auch ein-Steuerelement hinzufügen, <xref:Microsoft.Office.Tools.Excel.NamedRange> indem Sie es aus der **Toolbox** auf das Arbeitsblatt ziehen.

 In diesem Schritt fügen Sie dem Arbeitsblatt mithilfe der **Toolbox** zwei benannte Bereichs Steuerelemente hinzu, und fügen dann dem Arbeitsblatt Text hinzu.

### <a name="to-add-a-range-to-your-worksheet"></a>So fügen Sie dem Arbeitsblatt einen Bereich hinzu

1. Überprüfen Sie, ob der *benannte Bereich Events.xlsx* Arbeitsmappe im Visual Studio-Designer geöffnet ist, und wird `Sheet1` angezeigt.

2. Ziehen Sie aus der Registerkarte Excel-Steuer **Elemente** der Toolbox ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement in die Zelle **a1** in `Sheet1` .

     Das Dialogfeld **NamedRange-Steuerelement hinzufügen** wird angezeigt.

3. Vergewissern Sie sich, dass **$A $1** im bearbeitbaren Textfeld angezeigt wird und dass Zelle **a1** ausgewählt ist. Wenn dies nicht der Fall ist, klicken Sie auf Zelle **a1** , um Sie auszuwählen.

4. Klicken Sie auf **OK**.

     Zelle **a1** wird zu einem Bereich mit dem Namen `namedRange1` . Es gibt keinen sichtbaren Hinweis auf das Arbeitsblatt, wird jedoch `namedRange1` im Feld **Name** angezeigt (befindet sich auf der linken Seite direkt über dem Arbeitsblatt), wenn Zelle **a1** ausgewählt ist.

5. Fügen Sie der <xref:Microsoft.Office.Tools.Excel.NamedRange> Zelle **B3** ein weiteres Steuerelement hinzu.

6. Vergewissern Sie sich, dass **$B $3** im bearbeitbaren Textfeld angezeigt wird und dass Zelle **B3** ausgewählt ist. Wenn dies nicht der Fall ist, klicken Sie auf Zelle **B3** , um Sie auszuwählen.

7. Klicken Sie auf **OK**.

     Zelle **B3** wird zu einem Bereich mit dem Namen `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>So fügen Sie dem Arbeitsblatt Text hinzu

1. Geben Sie in Zelle **a1** den folgenden Text ein:

    **Dies ist ein Beispiel für ein Name Drange-Steuerelement.**

2. Geben Sie in Zelle **a3** (auf der linken Seite von `namedRange2` ) den folgenden Text ein:

    **Fall**

   In den folgenden Abschnitten schreiben Sie Code, der `namedRange2` `namedRange2` in Reaktion auf die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> -,-und- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignisse von Text in einfügt und Eigenschaften des-Steuer Elements ändert `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Fügen Sie Code hinzu, um auf das BeforeDoubleClick-Ereignis zu reagieren.

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>So fügen Sie Text in namedRange2 basierend auf dem BeforeDoubleClick-Ereignis ein

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1. vb** oder **Sheet1.cs** , und wählen Sie **Code anzeigen** aus.

2. Fügen Sie Code hinzu, damit der `namedRange1_BeforeDoubleClick` Ereignishandler wie folgt aussieht:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. In c# müssen Sie Ereignishandler für den benannten Bereich hinzufügen, wie im nachfolgenden <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis gezeigt. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Hinzufügen von Code, um auf das Änderungs Ereignis zu reagieren

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>So fügen Sie Text in namedRange2 basierend auf dem Änderungs Ereignis ein

1. Fügen Sie Code hinzu, damit der `NamedRange1_Change` Ereignishandler wie folgt aussieht:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Da das Doppelklicken auf eine Zelle in einem Excel-Bereich in den Bearbeitungsmodus wechselt, tritt ein-Ereignis auf, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Wenn die Auswahl außerhalb des Bereichs verschoben wird, auch wenn keine Textänderungen aufgetreten sind.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Fügen Sie Code hinzu, um auf das SelectionChange-Ereignis zu reagieren

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>So fügen Sie Text in namedRange2 basierend auf dem SelectionChange-Ereignis ein

1. Fügen Sie Code hinzu, damit der **NamedRange1_SelectionChange** Ereignishandler wie folgt aussieht:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Da das Doppelklicken auf eine Zelle in einem Excel-Bereich bewirkt, dass die Auswahl in den Bereich wechselt, tritt ein-Ereignis auf, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> bevor das- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> Ereignis auftritt.

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie die Arbeitsmappe testen, um zu überprüfen, ob Text, der die Ereignisse eines Steuer Elements beschreibt, <xref:Microsoft.Office.Tools.Excel.NamedRange> in einen anderen benannten Bereich eingefügt wird, wenn die Ereignisse ausgelöst werden.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Platzieren Sie den Cursor in `namedRange1` , und überprüfen Sie, ob der Text bezüglich des <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignisses eingefügt und ein Kommentar in das Arbeitsblatt eingefügt wird.

3. Doppelklicken Sie `namedRange1` in, und überprüfen Sie, ob der Text bezüglich der <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> Ereignisse mit rotem kursiv gelegtem Text in eingefügt wird `namedRange2` .

4. Klicken Sie außerhalb von `namedRange1` , und beachten Sie, dass das Änderungs Ereignis beim Beenden des Bearbeitungsmodus auftritt, obwohl keine Änderung an dem Text vorgenommen wurde.

5. Ändern Sie den Text in `namedRange1` .

6. Klicken Sie außerhalb von `namedRange1` , und überprüfen Sie, ob der Text bezüglich des <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Ereignisses mit blauem Text in eingefügt wird `namedRange2` .

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Programmierung für Ereignisse eines- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuer Elements. Dies ist eine Aufgabe, die als nächstes angezeigt werden kann:

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)
