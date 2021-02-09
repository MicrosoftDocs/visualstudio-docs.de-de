---
title: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe der Schaltfläche
description: Erfahren Sie mehr über die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Microsoft Excel-Arbeitsblättern. Erstellen Sie auch Excel-Projekte mithilfe der Office-Entwicklungs Tools in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 270754005704d91569f014ed2e0be382bc2dd707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906473"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche
  In dieser exemplarischen Vorgehensweise werden die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Microsoft Office Excel-Arbeitsblättern und das Erstellen von Excel-Projekten mithilfe von Office-Entwicklungs Tools in Visual Studio erläutert. Das Ergebnis als vollständiges Beispiel finden Sie im Beispiel für Excel-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Fügen Sie einem Arbeitsblatt Steuerelemente hinzu.

- Füllt ein Textfeld auf, wenn auf eine Schaltfläche geklickt wird.

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

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **Meine Excel-Schaltfläche**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt das Projekt " **Meine Excel-Schaltfläche** " **Projektmappen-Explorer** hinzu.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 In dieser exemplarischen Vorgehensweise benötigen Sie eine Schaltfläche und ein Textfeld auf dem ersten Arbeitsblatt.

### <a name="to-add-a-button-and-a-text-box"></a>So fügen Sie eine Schaltfläche und ein Textfeld hinzu

1. Überprüfen Sie, ob die Arbeitsmappe **Meine Excel-Button.xlsx** im Visual Studio-Designer geöffnet ist, und wird `Sheet1` angezeigt.

2. Ziehen Sie auf der Registerkarte **Allgemeine Steuerelemente** der Toolbox <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> auf `Sheet1` .

3. Wählen Sie im Menü **Ansicht** die Option **Eigenschaften Fenster** aus.

4. Stellen Sie sicher, dass **TextBox1** im Dropdown Feld **Eigenschaften** Fenster sichtbar ist, und ändern Sie die **Name** -Eigenschaft des Textfelds in **DisplayText**.

5. Ziehen Sie ein **Button** -Steuerelement auf, `Sheet1` und ändern Sie die folgenden Eigenschaften:

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Text einfügen**|

   Schreiben Sie nun den Code, der ausgeführt wird, wenn auf die Schaltfläche geklickt wird.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Textfeld auffüllen, wenn auf die Schaltfläche geklickt wird
 Jedes Mal, wenn der Benutzer auf die Schaltfläche klickt, **Hallo Welt!** wird an das Textfeld angehängt.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler der Schaltfläche den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. In c# müssen Sie dem-Ereignis einen Ereignishandler hinzufügen, <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> wie unten gezeigt. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können Ihre Arbeitsmappe jetzt testen, um sicherzustellen, dass die Nachricht **Hallo Welt!** wird im Textfeld angezeigt, wenn Sie auf die Schaltfläche klicken.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Klicken Sie auf die Schaltfläche.

3. Vergewissern Sie sich, dass **Hallo Welt!** wird im Textfeld angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

- Verwenden Sie Kontrollkästchen, um die Formatierung zu ändern. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Ändern der Arbeitsblatt Formatierung mithilfe von CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)-Steuerelementen.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Exemplarische Vorgehensweisen mit Excel](../vsto/walkthroughs-using-excel.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
