---
title: Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit
description: Erfahren Sie, wie Sie einem Microsoft Office Word-Dokument und Microsoft Office Excel-Arbeitsmappe zur Laufzeit Steuerelemente hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d49c7fa9224b2d527956536cb0c56b016f6b52e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948647"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit
  Sie können einem Microsoft Office Word-Dokument und einer Microsoft Office Excel-Arbeitsmappe Steuerelemente zur Laufzeit hinzufügen. Sie können sie auch zur Laufzeit entfernen. Steuerelemente, die Sie zur Laufzeit hinzufügen oder entfernen, heißen *dynamische Steuerelemente*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 In diesem Thema wird Folgendes beschrieben:

- [Verwalten von Steuerelementen zur Laufzeit mithilfe von Steuerelement Auflistungen](#ControlsCollection).

- [Fügen Sie den Dokumenten Host Steuerelemente hinzu](#HostControls).

- [Fügen Sie Dokumenten Windows Forms-Steuerelemente hinzu](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Verwalten von Steuerelementen zur Laufzeit mithilfe von Steuerelement Auflistungen
 Verwenden Sie zum Hinzufügen, Abrufen oder Entfernen von Steuerelementen zur Laufzeit Hilfsmethoden der Objekte <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> .

 Wie Sie auf diese Objekte zugreifen, hängt vom Typ des Projekts ab, das Sie entwickeln:

- In einem Projekt auf Dokumentebene für Excel verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> -Eigenschaft der Klassen `Sheet1`, `Sheet2`und `Sheet3` . Weitere Informationen zu diesen Klassen finden Sie unter [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md).

- In einem Projekt auf Dokumentebene für Word verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> -Eigenschaft der `ThisDocument` -Klasse. Weitere Informationen zu dieser Klasse finden Sie unter [Dokument Host Element](../vsto/document-host-item.md).

- Verwenden Sie in einem VSTO-Add-in-Projekt für Excel oder Word die- `Controls` Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> , das Sie zur Laufzeit generieren. Weitere Informationen zum Erstellen dieser Objekte zur Laufzeit finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Hinzufügen von Steuerelementen
 Die Typen <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> enthalten Hilfsmethoden, mit denen Sie Dokumenten und Arbeitsblättern Hoststeuerelemente und allgemeine Windows Forms-Steuerelemente hinzufügen können. Jeder Methodenname weist folgendes Format auf `Add`*Steuerelementklasse*. Dabei ist *Steuerelementklasse* der Klassenname des Steuerelements, das Sie hinzufügen möchten. Verwenden Sie beispielsweise zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelements zu Ihrem Dokument die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> -Methode.

 Im folgenden Codebeispiel wird in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> zu `Sheet1` hinzugefügt.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Zugriffs-und Lösch Steuerelemente
 Sie können Sie `Controls`-Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> verwenden, um alle Steuerelemente in Ihrem Dokument zu durchlaufen, auch die zur Entwurfszeit hinzugefügten. Steuerelemente, die zur Entwurfszeit hinzufügt werden, werden auch als *statische Steuerelemente* bezeichnet.

 Sie können dynamische Steuerelemente entfernen, indem Sie die- `Delete` Methode des-Steuer Elements aufrufen, oder indem Sie die-Methode jeder Steuerelement Auflistung aufrufen `Remove` . Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> -Methode verwendet, um in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> aus `Sheet1` zu entfernen.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Statische Steuerelemente können nicht zur Laufzeit entfernt werden. Wenn Sie versuchen, ein statisches Steuerelement mit der `Delete`- oder der `Remove`-Methode zu entfernen, wird eine <xref:Microsoft.Office.Tools.CannotRemoveControlException> ausgelöst.

> [!NOTE]
> Vermeiden Sie es, Steuerelemente im `Shutdown` -Ereignishandlerzeitraum des Dokuments programmgesteuert zu entfernen. Die Benutzeroberflächenelemente des Dokuments sind nicht mehr verfügbar, wenn das `Shutdown` -Ereignis ausgelöst wird. Wenn Sie Steuerelemente vor dem Schließen des Dokuments entfernen möchten, fügen Sie den Code dem Ereignishandler für ein anderes Ereignis hinzu, z. B. <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> oder <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> für Word oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> für Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Hinzufügen von Host Steuerelementen zu Dokumenten

Wenn Sie Dokumenten programmgesteuert Hoststeuerelemente hinzufügen, müssen Sie einen Namen angeben, der das Steuerelement eindeutig identifiziert, und Sie müssen angeben, wo das Steuerelement im Dokument hinzugefügt werden soll. Spezifische Anweisungen finden Sie unter den folgenden Themen:

- [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Gewusst wie: Hinzufügen von Diagramm Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Gewusst wie: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Weitere Informationen zu Host Steuerelementen finden Sie unter [Übersicht über Host Elemente und Host](../vsto/host-items-and-host-controls-overview.md)Steuerelemente.

Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Hoststeuerelemente von ihren Ereignissen getrennt und verlieren ihre Datenbindungsfunktion. Sie können der Projektmappe Code hinzufügen, damit die Hoststeuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Weitere Informationen finden Sie unter persistente [dynamische Steuerelemente in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Für folgende Hoststeuerelemente werden keine Hilfsmethoden bereitgestellt, da diese Steuerelemente nicht programmgesteuert Dokumenten hinzugefügt werden können: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>und <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Hinzufügen von Windows Forms Steuerelementen zu Dokumenten
 Wenn Sie einem Dokument programmgesteuert ein Windows Forms-Steuerelement hinzufügen, müssen Sie die Position des Steuerelements und einen Namen angeben, der das Steuerelement eindeutig identifiziert. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stellt Hilfsmethoden für jedes Steuerelement bereit. Diese Methoden werden überladen, sodass Sie entweder einen Bereich oder bestimmte Koordinaten für die Position des Steuerelements übergeben können.

 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Windows Forms-Steuerelemente aus dem Dokument entfernt. Sie können der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Wenn Sie dynamische Windows Forms Steuerelemente mithilfe eines VSTO-Add-Ins erstellen, verbleiben die ActiveX-Wrapper für die Steuerelemente im Dokument. Weitere Informationen finden Sie unter persistente [dynamische Steuerelemente in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Windows Forms-Steuerelemente können geschützten Dokumenten nicht programmgesteuert hinzugefügt werden. Wenn Sie den Schutz eines Word-Dokuments oder Excel-Arbeitsblatts programmgesteuert aufheben, um ein Steuerelement hinzuzufügen, müssen Sie zusätzlichen Code zum Entfernen des ActiveX-Wrappers des Steuerelements beim Schließen des Dokuments schreiben. Der ActiveX-Wrapper des Steuerelements wird nicht automatisch aus geschützten Dokumenten gelöscht.

### <a name="add-custom-controls"></a>Hinzufügen von benutzerdefinierten Steuerelementen
 Wenn Sie ein <xref:System.Windows.Forms.Control> hinzufügen möchten, das von den verfügbaren Hilfsmethoden nicht unterstützt wird, z. B. ein benutzerdefiniertes Benutzersteuerelement, verwenden Sie folgende Methoden:

- Verwenden Sie für Excel eine der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Excel.ControlCollection> -Objekts.

- Verwenden Sie für Word eine der <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Word.ControlCollection> -Objekts.

  Übergeben Sie zum Hinzufügen des Steuerelements das <xref:System.Windows.Forms.Control>, eine Position für das Steuerelement und einen Namen, der das Steuerelement eindeutig identifiziert, an die `AddControl`-Methode. Die `AddControl`-Methode gibt ein Objekt zurück, das definiert, wie das Steuerelement mit dem Arbeitsblatt oder dem Dokument interagiert. Die- `AddControl` Methode gibt einen <xref:Microsoft.Office.Tools.Excel.ControlSite> (für Excel) oder ein- <xref:Microsoft.Office.Tools.Word.ControlSite> Objekt (für Word) zurück.

  Im folgenden Codebeispiel wird veranschaulicht, wie Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methode verwenden, um ein benutzerdefiniertes Steuerelement dynamisch zu einem Arbeitsblatt in einem Excel-Projekt auf Dokumentebene hinzuzufügen. In diesem Beispiel heißt das Benutzersteuerelement `UserControl1`, und der <xref:Microsoft.Office.Interop.Excel.Range> heißt `range1`. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von einer `Sheet`*n* -Klasse im Projekt aus.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Member benutzerdefinierter Steuerelemente verwenden
 Nachdem Sie mit einer der `AddControl`-Methoden einem Arbeitsblatt oder Dokument ein Steuerelement hinzugefügt haben, verfügen Sie nun über zwei verschiedene Steuerelementobjekte:

- das <xref:System.Windows.Forms.Control> -Objekt, das das benutzerdefinierte Steuerelement darstellt, und

- das `ControlSite`-, das `OLEObject` oder das `OLEControl`-Objekt, das das Steuerelement nach dem Hinzufügen zum Arbeitsblatt oder Dokument darstellt.

  Viele Eigenschaften und Methoden werden von diesen Steuerelementen gemeinsam verwendet. Es ist wichtig, dass Sie auf diese Member über das entsprechende Steuerelement zugreifen können:

- Verwenden Sie zum Zugreifen auf Member, die nur zum benutzerdefinierten Steuerelement gehören, <xref:System.Windows.Forms.Control>.

- Verwenden Sie zum Zugreifen auf Member, die von den Steuerelementen gemeinsam genutzt werden, das `ControlSite`-, das `OLEObject` oder das `OLEControl`-Objekt.

  Wenn Sie auf einen gemeinsam genutzten Member über das <xref:System.Windows.Forms.Control>zugreifen, schlägt dieser möglicherweise ohne Warnung oder Benachrichtigung fehl, oder es werden ungültige Ergebnisse erzeugt. Verwenden Sie stets Methoden oder Eigenschaften des `ControlSite`-, des `OLEObject`- oder des `OLEControl`-Objekts, es sei denn, die benötigte Methode oder Eigenschaft ist nicht verfügbar; nur in diesem Fall sollten Sie auf <xref:System.Windows.Forms.Control> verweisen.

  Sowohl die <xref:Microsoft.Office.Tools.Excel.ControlSite>-Klasse als auch die <xref:System.Windows.Forms.Control>-Klasse weisen eine `Top`-Eigenschaft auf. Verwenden Sie zum Abrufen oder Festlegen des Abstands zwischen dem oberen Rand des Steuerelements und dem oberen Rand des Dokuments die <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> -Eigenschaft von <xref:Microsoft.Office.Tools.Excel.ControlSite>anstelle der <xref:System.Windows.Forms.Control.Top%2A> -Eigenschaft von <xref:System.Windows.Forms.Control>.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Weitere Informationen
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Beibehalten dynamischer Steuerelemente in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Gewusst wie: Hinzufügen von Diagramm Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Gewusst wie: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
