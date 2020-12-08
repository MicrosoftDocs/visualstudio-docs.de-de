---
title: 'Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern'
description: Erfahren Sie, wie Sie einem Microsoft Office Excel-Arbeitsblatt in Projekten auf Dokument Ebene zur Entwurfszeit und zur Laufzeit NamedRange-Steuerelemente hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 54487ed7f7cdcb7e7da024e4b96fcbb6d5c2cfe4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848143"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern
  Sie können <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente in einem Microsoft Office Excel-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Projekten auf Dokumentebene hinzufügen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Sie können auch <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelemente zur Laufzeit in VSTO-Add-In-Projekten hinzufügen.

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von Name Drange-Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von Name Drange-Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene](#runtimedoclevel)

- [Hinzufügen von Name Drange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelementen finden Sie [unter Name Drange Control](../vsto/namedrange-control.md).

## <a name="add-namedrange-controls-at-design-time"></a><a name="designtime"></a> Hinzufügen von Name Drange-Steuerelementen zur Entwurfszeit
 Es gibt verschiedene Möglichkeiten zum Hinzufügen von <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelementen zur Entwurfszeit zu Arbeitsblättern in einem Projekt auf Dokumentebene: in Excel, über die **Toolbox** von Visual Studio oder im Fenster **Datenquellen** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>So fügen Sie ein NamedRange-Steuerelement mit dem Feld „Name“ zu einem Arbeitsblatt in Excel hinzu

1. Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.

2. Geben Sie im **Feld Name** einen Namen für den Bereich ein, und drücken **Sie die Eingabe** Taste.

     Das **Namenfeld** befindet sich neben der Bearbeitungsleiste genau über Spalte **A** des Arbeitsblatts.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>So fügen Sie ein NamedRange-Steuerelement mit der Toolbox zu einem Arbeitsblatt hinzu

1. Öffnen Sie die **Toolbox** , und klicken Sie auf die Registerkarte **Excel-Steuerelemente** .

2. Klicken Sie auf <xref:Microsoft.Office.Tools.Excel.NamedRange> , und ziehen Sie es in ein Arbeitsblatt.

     Das Dialogfeld **Benannten Bereich hinzufügen** wird angezeigt.

3. Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.

4. Klicken Sie auf **OK**.

     Wenn Sie nicht den Standardnamen für das Steuerelement verwenden möchten, können Sie den Namen im **Eigenschaftenfenster** ändern.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>So fügen Sie ein NamedRange-Steuerelement über das Fenster „Datenquellen“ zu einem Arbeitsblatt hinzu

1. Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

2. Ziehen Sie ein einzelnes Feld aus dem Fenster **Datenquellen** in das Arbeitsblatt.

     Ein datengebundenes <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement wird dem Arbeitsblatt hinzugefügt. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Hinzufügen von Name Drange-Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene
 Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement programmgesteuert zur Laufzeit zum Arbeitsblatt hinzufügen. So können Sie Hoststeuerelemente als Antwort auf Ereignisse erstellen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein NamedRange-Steuerelement programmgesteuert hinzu

1. Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> -Ereignishandler von `Sheet1`den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zu Zelle **A1** hinzuzufügen, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft auf `Hello world!`fest.

     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]

## <a name="add-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Hinzufügen von Name Drange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO-Add-In-Projekt hinzufügen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein NamedRange-Steuerelement programmgesteuert hinzu

1. Der folgende Code generiert ein Arbeitsblatthostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1** hinzu, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft auf `Hello world`fest.

     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]

## <a name="see-also"></a>Siehe auch
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Gewusst wie: Ändern der Größe von Name Drange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
