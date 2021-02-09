---
title: Aktionsbereich zu Word-Dokumenten oder Excel-Arbeitsmappen hinzufügen
description: Wenn Sie einem Microsoft Office Word-Dokument oder einer Microsoft Excel-Arbeitsmappe einen Aktionsbereich hinzufügen möchten, sollten Sie zunächst ein Windows Forms Benutzer Steuerelement erstellen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f9488a15f851446c5779bdb1a4572e69a1cf3053
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917528"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen
  Um einem Microsoft Office Word-Dokument oder einer Microsoft Excel-Arbeitsmappe einen Aktionsbereich hinzuzufügen, erstellen Sie zunächst ein Windows Forms Benutzer Steuerelement. Fügen Sie dann das Benutzer Steuerelement der- <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> Eigenschaft des `ThisDocument.ActionsPane` Felds (Word) oder `ThisWorkbook.ActionsPane` Feld (Excel) im Projekt hinzu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Erstellen des Benutzersteuerelements
 Im folgenden Verfahren wird gezeigt, wie ein Benutzer Steuerelement in einem Word-oder Excel-Projekt erstellt wird. Außerdem wird dem Benutzer Steuerelement eine Schaltfläche hinzugefügt, die Text in das Dokument oder die Arbeitsmappe schreibt, wenn darauf geklickt wird.

#### <a name="to-create-the-user-control"></a>So erstellen Sie das Benutzer Steuerelement

1. Öffnen Sie Ihr Word-oder Excel-Projekt auf Dokument Ebene in Visual Studio.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Aktionsbereich- **Steuer** Element aus, nennen Sie es **HelloControl**, und klicken Sie auf **Hinzufügen**.

    > [!NOTE]
    > Alternativ können Sie dem Projekt ein **Benutzer Steuer** Element hinzufügen. Die durch das Aktionsbereich- **Steuer** Element und die **Benutzer Steuer** Elemente generierten Klassen sind funktional äquivalent.

4. Ziehen Sie auf der Registerkarte **Windows Forms** der **Toolbox** ein **Schalt** Flächen-Steuerelement auf das-Steuerelement.

    > [!NOTE]
    > Wenn das Steuerelement im Designer nicht sichtbar ist, doppelklicken Sie in **Projektmappen-Explorer** auf **HelloControl** .

5. Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler der Schaltfläche den Code hinzu. Das folgende Beispiel zeigt Code für ein Microsoft Office Word-Dokument.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. In c# müssen Sie einen Ereignishandler für den Schaltflächen Klick hinzufügen. Sie können diesen Code nach dem-Befehl im- `HelloControl` Konstruktor platzieren `InitializeComponent` .

     Weitere Informationen zum Erstellen von Ereignis Handlern finden Sie unter Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Hinzufügen des Benutzer Steuer Elements zum Aktionsbereich
 Fügen Sie das Benutzer Steuerelement zur- <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> Eigenschaft des `ThisDocument.ActionsPane` Felds (Word) oder `ThisWorkbook.ActionsPane` Feld (Excel) hinzu, um den Aktionsbereich anzuzeigen.

### <a name="to-add-the-user-control-to-the-actions-pane"></a>So fügen Sie das Benutzer Steuerelement zum Aktionsbereich hinzu

1. Fügen Sie der-Klasse oder der-Klasse den folgenden Code `ThisDocument` `ThisWorkbook` als Deklaration auf Klassenebene hinzu (fügen Sie diesen Code nicht zu einer-Methode hinzu).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Fügen Sie dem- `ThisDocument_Startup` Ereignishandler der- `ThisDocument` Klasse oder dem- `ThisWorkbook_Startup` Ereignishandler der-Klasse `ThisWorkbook` den folgenden Code hinzu.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Gewusst wie: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
