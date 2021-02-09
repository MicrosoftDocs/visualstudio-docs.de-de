---
title: Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten
description: Erfahren Sie mehr über die Einschränkungen von Windows Forms Steuerungsmethoden und-Eigenschaften für Microsoft Office Dokumente.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc507d31f791a3f3d7addbcffc0b9b87963d443f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888718"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten

Es gibt einige Unterschiede zwischen Windows Forms-Steuerelementen, die Microsoft Office Word-Dokumenten hinzugefügt werden, oder Microsoft Office Excel-Arbeitsblätter und Windows Forms Steuerelemente, die Windows Forms hinzugefügt werden. Wenn Sie z. b. einem Dokument ein Steuerelement hinzufügen <xref:Microsoft.Office.Tools.Word.Controls.Button> , Verhalten sich Eigenschaften wie <xref:System.Windows.Forms.Control.Dock> , <xref:System.Windows.Forms.Control.Anchor> und <xref:System.Windows.Forms.Control.TabIndex> nicht wie erwartet.

Viele dieser Unterschiede sind darauf zurückzuführen, wie Windows Forms Steuerelemente in Dokumenten gehostet werden. Wenn einem Dokument ein Windows Forms-Steuerelement hinzugefügt wird, bettet ein ActiveX-Steuerelement ein, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] das dann das Windows Forms Steuerelement im Dokument hostet. Das Windows Forms-Steuerelement ist nicht direkt in das Dokument eingebettet.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Einschränkungen von Methoden und Eigenschaften von Windows Forms-Steuerelementen

Es gibt eine Reihe von Methoden und Eigenschaften von Windows Forms-Steuerelementen, die nicht auf die gleiche Weise in einem Dokument funktionieren wie in einem Windows Form. Daher wird empfohlen, dass Sie nicht verwendet werden. Beispielsweise wirkt sich das Festlegen von Eigenschaften wie <xref:System.Windows.Forms.Control.Dock> und <xref:System.Windows.Forms.Control.Anchor> nur auf die Position des Steuer Elements in Bezug auf das ActiveX-Steuerelement des Containers und nicht auf das Dokument aus. Im folgenden finden Sie eine Liste der nicht unterstützten Methoden und Eigenschaften von Windows Forms-Steuerelementen für Word und Excel:

- Nicht unterstützte Eigenschaften von Excel-Steuerelementen:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nicht unterstützte Methoden und Eigenschaften von Word-Steuerelementen:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Sie können auch nicht die- <xref:System.Windows.Forms.Control.Left> Eigenschaft oder die- <xref:System.Windows.Forms.Control.Top> Eigenschaft von Windows Forms-Steuerelementen festlegen, die mit Text in einem Word-Dokument übereinstimmen. Windows Forms-Steuerelemente werden in den folgenden Fällen in der Zeile mit Text hinzugefügt:

- Sie können einem Word-Dokument Programm gesteuert ein-Steuerelement hinzufügen und eine-Methode verwenden, die einen Bereich für den Speicherort angibt.

- Sie können einem Word-Dokument zur Entwurfszeit ein Windows Forms-Steuerelement hinzufügen. Sie können dies ändern, indem Sie das-Steuerelement im-Designer ändern.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Unterschiede bei Windows Forms-Steuerelementen in Office-Dokumenten

Windows Forms Steuerelemente haben im Allgemeinen das gleiche Verhalten wie in einem Windows Form in einem Office-Dokument, aber es gibt einige Unterschiede. In der folgenden Tabelle werden die Unterschiede beschrieben, die für Windows Forms Steuerelemente in Office-Dokumenten bestehen.

|Funktionalität|Unterschied|
|-------------------|----------------|
|Registerkarten Reihenfolge|Sie können keine Tabstopps durch Steuerelemente auf einem Excel-Arbeitsblatt oder Word-Dokument ablegen.|
|Steuerelement Gruppierung|Ein Steuerelement kann nicht verwendet werden <xref:System.Windows.Forms.GroupBox> , um andere Steuerelemente in einem Office-Dokument aufzunehmen. Wenn Sie dem Dokument mehrere Options Felder direkt hinzufügen, schließen sich die Options Felder nicht gegenseitig aus. Sie können Code schreiben, um die Options Felder gegenseitig zu schließen. die bevorzugte Vorgehensweise besteht jedoch darin, einem Benutzer Steuerelement die Options Felder hinzuzufügen und dann dem Dokument das Benutzer Steuerelement hinzuzufügen. Weitere Informationen finden Sie im Beispiel Word-Steuerelemente oder Excel-Steuerelemente unter [Office-Entwicklungs Beispiele und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.|
|Steuerelementtyp|Windows Forms Steuerelemente, die für Dokumente verwendet werden, sind in einer Klasse enthalten, die von bereitgestellt wird [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , die den Steuerelementen zusätzliche Funktionen für das Excel-Arbeitsblatt oder Word-Dokument bietet Wenn Sie z. b. ein **Schalt** Flächen-Steuerelement auf einem Excel-Arbeitsblatt haben, achten Sie darauf, dass Sie den Typ als angeben, <xref:Microsoft.Office.Tools.Excel.Controls.Button> anstatt auf <xref:System.Windows.Forms.Button> das Objekt zu verweisen oder es zu konvertieren.|
|Position und Größe des Steuer Elements|Die Größe und die Position des Steuer Elements werden durch Eigenschaften bestimmt, die Teil des ActiveX-Steuer Elements für den Container sind. Die ActiveX-Steuerelement Eigenschaften nehmen andere Werte als die entsprechenden Eigenschaften eines Windows Forms Steuer Elements. Wenn Sie die `Top` Eigenschaften, `Left` , `Height` oder eines-Steuer Elements festlegen `Width` , wird es in Punkten anstatt in Pixel gemessen.|
|Steuerelement Position in Word-Dokumenten|Wenn Sie einem Fluss basierten Layout Steuerelemente hinzufügen, denken Sie daran, dass die Steuerelemente mit dem Inhalt durchlaufen werden, wenn sich der Inhalt ändert. Sie können das Steuerelement nicht an einen Absatz anfügen, wenn Sie es aus der **Toolbox** ziehen, da das Steuerelement dem Word-Dokument in der Zeile mit Text hinzugefügt wird. Wenn Sie das Steuerelement mit einer anderen Methode hinzufügen, z. b. durch Doppelklicken auf das Steuerelement, wird das Steuerelement entsprechend der Word-Option eingefügt, die Sie zum Einfügen von Bildern festgelegt haben.<br /><br /> Sie können die- `Left` Eigenschaft oder die- `Top` Eigenschaft eines Steuer Elements, das Inline mit Text ist, nicht festlegen.<br /><br /> Sie können Steuerelemente nicht in einer Kopf-oder Fußzeile oder in einem unter Dokument platzieren.|
|Steuerelement Ereignisse|Wenn das Steuerelement ausgewählt ist, werden Ereignisse in der folgenden Reihenfolge ausgelöst:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Wenn das Steuerelement deaktiviert wird, werden Ereignisse in der folgenden Reihenfolge ausgelöst:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Steuern der Skalierung|Wenn Sie die Zoomeinstellung eines Dokuments in einen anderen Wert als 100% ändern, sind die Steuerelemente deaktiviert, obwohl Sie anscheinend mit dem Dokument skaliert werden. Wenn Sie z. b. auf eine Schaltfläche klicken, wenn das Dokument einen Zoom Wert von 130% aufweist, wird eine Meldung angezeigt, dass das Steuerelement deaktiviert wurde, bis der Zoom Wert auf 100% festgelegt ist. Die Steuerelemente funktionieren ordnungsgemäß, wenn Sie den Zoom Wert auf 100% ändern.|
|Steuerelement Eigenschaftswerte|Obwohl die Eigenschaften von Steuerelementen in einem Windows Form auf einen ganzzahligen Wert festgelegt sind, werden Sie auf einen einzelnen für Steuerelemente in einem Word-Dokument festgelegt. In Excel werden die Eigenschaftswerte von Steuerelementen auf einen Double-Wert festgelegt. Wenn die `Height` -Eigenschaft und die- `Width` Eigenschaft eines-Steuer Elements auf einem Arbeitsblatt die Größe des Arbeitsblatts oder Bildschirms überschreiten, wird der Wert abgeschnitten.|
|Größe des Steuer Elements ändern|Wenn Sie die Größe eines Steuer Elements im Dokument mit einem der acht Zieh Punkte ändern, werden die neuen Steuerelement Dimensionen nicht im **Eigenschaften** Fenster angezeigt, bis das Steuerelement erneut ausgewählt wird.|
|Steuerelement Verhalten|Steuerelemente auf einem Excel-Arbeitsblatt können sich möglicherweise unvorhersehbar Verhalten, wenn das Arbeitsblatt Fenster geteilt wird. Beispielsweise ist der Zugriff auf ein <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> auf dem Arbeitsblatt möglicherweise nur in einem der Fenster verfügbar.|
|Benennen von Steuerelementen|Sie können keine reservierten Wörter verwenden, um Steuerelemente zu benennen. Wenn Sie z. b. einem <xref:Microsoft.Office.Tools.Excel.Controls.Button> Arbeitsblatt eine hinzufügen und den Namen in **System** ändern, treten beim Erstellen des Projekts Fehler auf.|
|Programmgesteuerte Hinzufügen von Steuerelementen|Verwenden Sie den Konstruktor des Steuer Elements nicht, um dem Dokument zur Laufzeit ein Steuerelement hinzuzufügen. Verwenden Sie stattdessen die Hilfsmethoden, die von bereitgestellt werden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Verwenden Sie z. b <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> . die-Methode, um einem Arbeitsblatt eine Schaltfläche hinzuzufügen. Wenn Sie ein Steuerelement hinzufügen möchten, das von diesen Hilfsmethoden nicht unterstützt wird, können Sie die- `AddControl` Methode verwenden. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopieren von Steuerelementen|Wenn Sie ein Windows Forms Steuerelement kopieren und es zur Laufzeit in ein Dokument einfügen, wird ein leeres Container-ActiveX-Steuerelement in das Dokument eingefügt. Das Windows Forms Steuerelement wird nicht am neuen Speicherort angezeigt, und der Code hinter dem ursprünglichen Steuerelement wird nicht in das ActiveX-Steuerelement des Containers kopiert.|

## <a name="limitations-in-document-level-projects"></a>Einschränkungen in Projekten auf Dokument Ebene

Einige Einschränkungen bei der Verwendung von Windows Forms Steuerelementen in Dokumenten gelten nur für Projekte auf Dokument Ebene.

### <a name="control-support-at-design-time"></a>Steuern der Unterstützung zur Entwurfszeit

Bestimmte Windows Forms Steuerelemente werden aus der **Toolbox** entfernt, wenn ein Excel-Arbeitsblatt oder Word-Dokument im Visual Studio-Designer geöffnet ist. Dies liegt an technischen Einschränkungen oder daran, dass die Funktionalität bereits in Word oder Excel verfügbar ist. Excel-und Word-Projekte unterstützen alle Windows Forms-Steuerelemente und andere Komponenten, die in der **Toolbox** angezeigt werden, wenn das Dokument den Fokus besitzt, und Sie können einem Arbeitsblatt oder einem Dokument auch Steuerelemente von Drittanbietern hinzufügen.

> [!NOTE]
> Wenn ein Dokument geschützt ist, werden alle Steuerelemente aus der **Toolbox** entfernt. Informationen zum Schutz von Dokumenten finden Sie unter [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Für Steuerelemente von Drittanbietern muss das- <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut auf **true** festgelegt sein, damit Sie in einer Office-Projekt Mappe verwendet werden können.

Die folgenden Steuerelemente und Komponenten sind nicht in der **Toolbox** verfügbar:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Unterstützung für ältere ActiveX-Steuerelemente

Wenn Sie ein Office-Projekt auf Dokument Ebene erstellen, das ein vorhandenes Word-Dokument oder eine Excel-Arbeitsmappe verwendet, die ActiveX-Steuerelemente enthält, gehen die Funktionen der ActiveX-Steuerelemente nicht verloren. Es gibt jedoch keine Unterstützung für das Hinzufügen von neuen ActiveX-Steuerelementen zu Ihren Dokumenten aus Visual Studio. Wenn das Word-Dokument z. b. eine Schaltfläche aus der **Steuer** Element-Toolbox enthält, die ein Visual Basic for Applications-Makro (VBA) ausführt, wird das Makro weiter ausgeführt, nachdem das Dokument in einem Office-Projekt verwendet wurde. Es wird jedoch empfohlen, ActiveX-Steuerelemente und VBA-Makros zu entfernen und Sie durch Windows Forms Steuerelemente und verwalteten Code zu ersetzen.

## <a name="see-also"></a>Weitere Informationen

- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
