---
title: 'Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten'
description: Erfahren Sie, wie Sie in Projekten auf Dokument Ebene zur Entwurfszeit Microsoft Office Excel-und Microsoft Office Word-Dokumenten Windows Forms Steuerelemente hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8f073a72db1a18574dff6ab060b1ea069475fbb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846778"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten
  Sie können Microsoft Office Excel- und Microsoft Office Word-Dokumenten Windows Forms-Steuerelemente in Projekten auf Dokumentebene zur Entwurfszeit hinzufügen. Zur Laufzeit können Sie Steuerelemente in Anpassungen auf Dokument Ebene und in VSTO-Add-Ins hinzufügen. Beispielsweise können Sie dem Arbeitsblatt ein-Steuerelement hinzufügen, <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> damit Benutzer aus einer Liste von Optionen auswählen können.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von Steuerelementen zur Laufzeit in Projekten auf Dokument Ebene](#runtimedoclevel)

- [Hinzufügen von Steuerelementen zur Laufzeit in VSTO-Add-ins](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Hinzufügen von Steuerelementen zur Entwurfszeit
 Es gibt mehrere Möglichkeiten, dem Dokument Windows Forms-Steuerelemente in einem Projekt auf Dokumentebene zur Entwurfszeit hinzuzufügen.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>So ziehen ein Windows Forms-Steuerelement auf das Dokument

1. Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten, und ziehen Sie es in das Dokument.

    > [!NOTE]
    > Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>So ziehen ein Windows Forms-Steuerelement auf das Dokument

1. Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.

3. Klicken Sie im Dokument auf die Stelle, an der die linke obere Ecke des Steuerelements positioniert werden soll, und ziehen Sie den Mauszeiger an die Stelle, an der sich die untere rechte Ecke des Steuerelements befinden soll.

     Das Steuerelement wird dem Dokument mit der angegebenen Größe und Position hinzugefügt.

    > [!NOTE]
    > Wenn Sie in Excel ein Steuerelement auswählen, wird **= embed ("WinForms. Control. Host", "")**  in der Bearbeitungs **Leiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement durch einfaches Klicken auf das Steuerelement hinzu

1. Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.

3. Klicken Sie im Dokument auf die Stelle, an der das Steuerelement hinzugefügt werden soll.

     Das Steuerelement wird dem Dokument mit der Standardgröße hinzugefügt.

    > [!NOTE]
    > Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement durch Doppelklicken auf das Steuerelement hinzu

1. Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Doppelklicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.

     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.

    > [!NOTE]
    > Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement hinzu, indem Sie die EINGABETASTE drücken

1. Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten, und drücken Sie die **Eingabe** Taste.

     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.

    > [!NOTE]
    > Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Hinzufügen von Steuerelementen zur Laufzeit in Projekten auf Dokument Ebene
 Sie können einem Dokument Windows Forms-Steuerelemente zur Laufzeit programmgesteuert hinzufügen. Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A>-Eigenschaft der `ThisDocument`-Klasse. Verwenden Sie in Excel die Methoden der- <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> Eigenschaft einer `Sheet` *n* -Klasse. Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.

 Wenn Sie einem Dokument ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird. Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>So fügen Sie ein Windows Forms-Steuerelement zur Laufzeit hinzu

1. Verwenden Sie eine Methode mit dem Namen Add \<*control class*> (wobei *Control-Klasse* der Klassenname des Windows Forms Steuer Elements ist, das Sie hinzufügen möchten, z <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> . b.).

     Im folgenden Codebeispiel wird veranschaulicht, wie Sie <xref:Microsoft.Office.Tools.Excel.Controls.Button> **C5** `Sheet1` in einem Projekt auf Dokument Ebene für Excel ein zu einer Zelle C5 von hinzufügen.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Hinzufügen von Steuerelementen zur Laufzeit in VSTO-Add-ins
 Sie können einem beliebigen geöffneten Dokument zur Laufzeit Windows Forms-Steuerelemente hinzufügen. Generieren Sie zuerst ein Hostelement, das auf einem geöffneten Dokument oder Arbeitsblatt basiert. Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>-Eigenschaft des neuen Hostelements. Verwenden Sie in Excel die Methoden der <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>-Eigenschaft des neuen Hostelements. Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.

 Wenn Sie einem Dokument ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird. Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Weitere Informationen zum Erstellen von Host Elementen in VSTO-Add-in-Projekten finden Sie [unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>So fügen Sie ein Windows Forms-Steuerelement zur Laufzeit hinzu

1. Verwenden Sie eine Methode mit dem Namen Add \<*control class*> (wobei *Control-Klasse* der Klassenname des Windows Forms Steuer Elements ist, das Sie hinzufügen möchten, z <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> . b.).

    > [!NOTE]
    > In VSTO-Add-in-Projekten, die auf oder höher ausgerichtet [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sind, müssen Sie einen Verweis auf die *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* oder *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* Assembly hinzufügen, bevor Sie auf die Add-Methoden zugreifen können \<*control class*> .

     Das folgende Codebeispiel veranschaulicht das Hinzufügen von <xref:Microsoft.Office.Tools.Word.Controls.Button> im ersten Absatz des aktiven Dokuments mithilfe eines Word-VSTO-Add-Ins.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Siehe auch
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
