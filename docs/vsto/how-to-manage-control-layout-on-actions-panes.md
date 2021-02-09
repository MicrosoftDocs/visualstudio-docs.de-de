---
title: 'Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen'
description: Erfahren Sie, wie Sie das Steuerelement Layout für Aktionsbereiche verwalten, indem Sie Code schreiben, um die Benutzer Steuerelemente ordnungsgemäß zu Stapeln
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49739b6011fcf977db84a3350929a56514040975
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918596"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen
  Ein Aktionsbereich wird standardmäßig rechts von einem Dokument oder Arbeitsblatt angedockt. Sie kann jedoch Links, oben oder unten angedockt werden. Wenn Sie mehrere Benutzer Steuerelemente verwenden, können Sie Code schreiben, um die Benutzer Steuerelemente im Aktionsbereich ordnungsgemäß zu stapeln. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Die Stapelreihenfolge der Steuerelemente hängt davon ab, ob der Aktionsbereich vertikal oder horizontal angedockt ist.

> [!NOTE]
> Wenn der Benutzer die Größe des Aktionsbereichs zur Laufzeit ändert, können Sie die Größe der Steuerelemente mit dem Aktionsbereich festlegen. Sie können die <xref:System.Windows.Forms.Control.Anchor%2A>-Eigenschaft eines Windows Forms-Steuerelements verwenden, um Steuerelemente im Aktionsbereich zu verankern. Weitere Informationen finden Sie unter Gewusst [wie: Verankern von Steuerelementen auf Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>So legen Sie die Stapelreihenfolge der Aktionsbereich-Steuerelemente fest

1. Öffnen Sie ein Projekt auf Dokument Ebene für Microsoft Office Word, das einen Aktionsbereich mit mehreren Benutzer Steuerelementen oder Steuerelementen für den Bereich "Bereich" enthält. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeits](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)Mappen.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument.cs** oder **ThisDocument. vb** , und klicken Sie dann auf **Code anzeigen**.

3. <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>Überprüfen Sie im Ereignishandler des Aktionsbereichs, ob die Ausrichtung des Aktionsbereichs horizontal ist.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Wenn die Ausrichtung horizontal ist, stapeln Sie die Steuerelemente des Aktionsbereichs von Links. Andernfalls stapeln Sie Sie von oben.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. In c# müssen Sie dem-Ereignishandler einen Ereignishandler für das Hinzufügen `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> . Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Führen Sie das Projekt aus, und überprüfen Sie, ob die Steuerelemente des Aktionsbereichs von links nach rechts gestapelt werden, wenn der Aktionsbereich am oberen Rand des Dokuments angedockt ist und die Steuerelemente von oben nach unten gestapelt werden, wenn der Aktionsbereich auf der rechten Seite des Dokuments angedockt ist.

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Ein Word-Projekt auf Dokument Ebene mit einem Aktionsbereich, der mehrere Benutzer Steuerelemente oder Bereiche des Bereichs "Bereich von Bereichen" enthält.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
