---
title: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche
description: Erfahren Sie, wie Sie Schaltflächen und Textfelder in einer Anpassung auf Dokument Ebene für Microsoft Word verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cda1fe3e7430ff30dcc3b3921eb2bcd4d31b699
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522748"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Schaltflächen und Textfeldern in einer Anpassung auf Dokumentebene für Microsoft Office Word beschrieben.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Steuerelementen zum Word-Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit

- Auffüllen eines Textfelds beim Klicken auf eine Schaltfläche

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Erstellen des Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Word-Dokument Projekt mit der **Schaltfläche "mein Wort** benennen". Wählen Sie im Assistenten **Neues Dokument erstellen** aus.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Schaltflächen Projekt **My Word** hinzu.

## <a name="add-controls-to-the-word-document"></a>Hinzufügen von Steuerelementen zum Word-Dokument
 Die Steuerelemente der Benutzeroberfläche umfassen eine Schaltfläche und ein Textfeld für das Word-Dokument.

### <a name="to-add-a-button-and-a-text-box"></a>So fügen Sie eine Schaltfläche und ein Textfeld hinzu

1. Stellen Sie sicher, dass das Dokument im Visual Studio-Designer geöffnet ist.

2. Ziehen Sie ein-Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** <xref:Microsoft.Office.Tools.Word.Controls.TextBox> auf das Dokument.

   > [!NOTE]
   > In Word werden Steuerelemente standardmäßig in einer Reihe mit Text abgelegt. Sie können die Art und Weise ändern, wie Steuerelemente und Shape-Objekte eingefügt werden, indem Sie den Standardwert auf der Registerkarte **Bearbeiten** des Dialog Felds **Optionen** in Word ändern.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

4. Suchen Sie im Dropdown Feld **Eigenschaften** Fenster nach **TextBox1** , und ändern Sie die **Name** -Eigenschaft des Textfelds in **DisplayText**.

5. Ziehen Sie ein **Schalt** Flächen-Steuerelement in das Dokument, und ändern Sie die folgenden Eigenschaften.

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Text einfügen**|

   Jetzt können Sie den Code schreiben, der beim Klicken auf die Schaltfläche ausgeführt wird.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Textfeld auffüllen, wenn auf die Schaltfläche geklickt wird
 Jedes Mal, wenn der Benutzer auf die Schaltfläche klickt, **Hallo Welt!** wird dem Textfeld hinzugefügt.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie dem <xref:System.Windows.Forms.Control.Click>-Ereignishandler der Schaltfläche den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. In C# müssen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>-Ereignis einen Ereignishandler für die Schaltfläche hinzufügen. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können Ihr Dokument nun testen, um sicherzustellen, dass die Nachricht **Hallo Welt!** wird im Textfeld angezeigt, wenn Sie auf die Schaltfläche klicken.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Klicken Sie auf die Schaltfläche.

3. Vergewissern Sie sich, dass **Hallo Welt!** wird im Textfeld angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Word-Dokumenten. Die folgenden Aufgaben könnten sich daran anschließen:

- Verwenden eines Kombinationsfelds zum Ändern der Formatierung. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Ändern der Dokument Formatierung mithilfe von CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)-Steuerelementen.

- Auswählen von Diagrammformaten mithilfe von Optionsfeldern. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Aktualisieren eines Diagramms in einem Dokument mithilfe](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)von Options Feldern.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
