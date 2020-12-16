---
title: Übersicht über Windows Forms Steuerelemente in Office-Dokumenten
description: Erfahren Sie, wie Windows Forms Steuerelemente Objekte sind, mit denen Benutzer interagieren können, um Daten einzugeben oder zu bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0309ea22444062b117d3684e32b56960585aa184
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527046"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Übersicht über Windows Forms Steuerelemente in Office-Dokumenten
  Windows Forms-Steuerelemente sind Objekte, mit denen Benutzer arbeiten können, um Daten einzugeben oder zu ändern. In Projekten auf Dokumentebene für Microsoft Office Excel und Microsoft Office Word können Sie dem Dokument oder der Arbeitsmappe in Ihrem Projekt zur Entwurfszeit Windows Forms-Steuerelemente hinzufügen, Sie können diese Steuerelemente aber auch zur Laufzeit programmgesteuert hinzufügen. Sie können diese Steuerelemente jedem geöffneten Dokument oder Arbeitsblatt zur Laufzeit in einem VSTO-Add-in für Excel oder Word Programm gesteuert hinzufügen.

 Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Verwenden von Windows Forms Steuerelementen

Sie können Windows Forms-Steuerelemente zu Dokumenten und anpassbbaren Benutzeroberflächenelementen (etwa Aktionsbereiche, benutzerdefinierte Aufgabenbereiche und Windows Forms) hinzufügen. In den meisten Fällen verhalten sich Windows Forms-Steuerelemente in Dokumenten genauso wie in diesen anderen Benutzeroberflächenelementen, es gibt aber auch einige Unterschiede. Weitere Informationen finden Sie unter [Einschränkungen von Windows Forms-Steuerelementen in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

Die Entscheidung, ob Sie Windows Forms-Steuerelemente einem Dokument oder einem anderen Benutzeroberflächenelement hinzufügen, ist von verschiedenen Faktoren abhängig. Wenn Sie die Benutzeroberfläche Ihrer Lösung entwerfen, sollten Sie die Nutzung von Windows Forms-Steuerelemente entsprechend den Beschreibungen in der folgenden Tabelle berücksichtigen.

Auf einem Dokument.
- Wenn Sie möchten, dass die Steuerelemente immer angezeigt werden.

- Wenn Sie möchten, dass Benutzer Daten direkt in das Dokument eingeben, beispielsweise in formularbasierten Dokumente, bei denen die Bearbeitungsoberfläche gesperrt ist.

- Wenn Sie möchten, dass die Steuerelemente an den Daten ausgerichtet im Dokument angezeigt werden sollen. Wenn Sie beispielsweise jeder Zeile eines Listenobjekts Schaltflächen hinzufügen, sollten diese an dem jeweiligen Listenelement ausgerichtet sein.

Im Aktionsbereich oder in einem benutzerdefinierten Aufgabenbereich.
- Wenn Sie dem Benutzer Kontextinformationen bereitstellen möchten.

- Wenn Sie nur die Ergebnisse im Dokument anzeigen möchten, nicht die Abfragesteuerelemente und -daten.

- Wenn Sie sicherstellen möchten, dass die Steuerelemente nicht mit dem Dokument gedruckt werden.

- Wenn Sie sicherstellen möchten, dass die Steuerelemente nicht die Ansicht des Dokuments beeinträchtigen.

Auf einem Windows Form.
- Wenn Sie die Größe der Benutzeroberfläche steuern möchten.

- Wenn Sie verhindern möchten, dass Benutzer Steuerelemente ausblenden oder löschen können.

- Wenn der Benutzer Daten eingeben soll und Sie verhindern möchten, dass das Dokument vor Empfang der Eingabe anderweitig bearbeitet wird.

## <a name="add-windows-forms-controls-programmatically"></a>Programm gesteuertes hinzufügen Windows Forms Steuerelemente
 Sie können Word-Dokumenten und Excel-Arbeitsblättern zur Laufzeit Windows Forms-Steuerelemente hinzufügen. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stellt Hilfsmethoden zum Hinzufügen der gängigsten Windows Forms-Steuerelemente bereit. Mit diesen Hilfsmethoden können Sie Office-Dokumenten schnell Steuerelemente hinzufügen und die Kombination aus Windows Forms-Steuerelementfunktionalität und Office-bezogener Funktionalität dieser Steuerelemente nutzen.

 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Verwenden von Windows Forms-Steuerelementen in Projekten auf Dokument Ebene
 Einige Aspekte der Verwendung von Windows Forms-Steuerelementen in Dokumenten gelten nur für Projekte auf Dokumentebene, die es Ihnen ermöglichen, die Benutzeroberfläche Ihres Dokuments mit Visual Studio-Designer zu entwerfen.

### <a name="create-custom-user-controls"></a>Erstellen von benutzerdefinierten Benutzer Steuerelementen
 Sie können Ihrem Projekt ein Benutzersteuerelement hinzufügen und das Steuerelement dann der **Toolbox** hinzufügen. Danach können Sie das Benutzersteuerelement direkt in der gleichen Weise auf das Dokument ziehen, in der Sie einem Dokument ein Windows Forms-Steuerelement hinzufügen. Es gibt einige Punkte zu beachten, wenn Sie Benutzersteuerelemente erstellen:

- Erstellen Sie kein **sealed** Benutzersteuerelement. Wenn Sie das Steuerelement auf ein Dokument ziehen, generiert Visual Studio eine Wrapperklasse, die aus dem Benutzersteuerelement abgeleitet wird, um das Steuerelement zu erweitern und seine Verwendung auf dem Dokument zu unterstützen. Wenn das Benutzersteuerelement **sealed** ist, kann Visual Studio die Wrapperklasse nicht generieren.

- Für Benutzersteuerelemente muss das <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attribut auf **true**. Bei Benutzersteuerelementen, die in einem Office-Projekt erstellt werden, ist dieses Attribut standardmäßig auf **true** festgelegt, aber bei Benutzersteuerelementen, die zu externen Projekten gehören, ist dieses Attribut möglicherweise nicht auf **true** festgelegt.

- Nachdem Sie dem Dokument ein Benutzersteuerelement hinzugefügt haben, dürfen Sie die <xref:System.Windows.Forms.UserControl> -Klasse weder umbenennen noch aus dem Projekt löschen. Müssen Sie den Namen eines Benutzersteuerelements ändern, müssen Sie es zunächst aus dem Dokument löschen. Danach können Sie es, sobald der Name geändert wurde, erneut hinzufügen.

### <a name="arrange-controls-at-design-time"></a>Anordnen von Steuerelementen zur Entwurfszeit
 Wenn Sie Word- und Excel-Dokumenten zur Entwurfszeit mehrere Steuerelemente hinzufügen, können Sie die Ausrichtung aller ausgewählten Steuerelemente in Visual Studio schnell mit den Symbolleisten **Microsoft Office Word** und **Microsoft Office Excel** festlegen. Diese Symbolleisten sind nur verfügbar, wenn ein Dokument oder Arbeitsblatt im Designer geöffnet ist.

 Wenn Sie mehrere Steuerelemente im Designer auswählen, können Sie die Steuerelemente mit den folgenden Schaltflächen auf diesen Symbolleisten anordnen:

- **Nach links ausrichten**

- **Zentriert**

- **Nach rechts ausrichten**

- **Nach oben ausrichten**

- **Mittig ausrichten**

- **Nach unten ausrichten**

- **Horizontalen Abstand ausgleichen**

- **Vertikalen Abstand ausgleichen**

> [!NOTE]
> In Word-Projekten sind diese Schaltflächen nur aktiviert, wenn die ausgewählten Steuerelemente nicht am Text ausgerichtet sind. Standardmäßig werden Steuerelemente, die Sie dem Dokument zur Entwurfszeit hinzufügen, am Text ausgerichtet.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Verhindern, dass alte Daten beim Laden in Excel-Arbeitsmappen angezeigt werden
 Wenn Sie Dokumenten oder Arbeitsmappen zur Entwurfszeit Windows Forms-Steuerelemente hinzufügen, verbleiben die Steuerelemente im Dokument, wenn der Benutzer das Dokument schließt. Steuerelemente, die zur Entwurfszeit hinzufügt wurden, werden auch als *statische* Steuerelemente bezeichnet.

 Wird eine Excel-Arbeitsmappe geöffnet, die ein statisches Steuerelement enthält, wird in der Arbeitsmappe solange eine Bitmap des Steuerelements in einem ActiveX-Steuerelement angezeigt, bis der Anpassungscode ausgeführt und das tatsächliche Steuerelement geladen wird. Diese Bitmap wird von Excel erstellt und bei jedem Speichern der Arbeitsmappe in der Arbeitsmappe gespeichert. Das Steuerelement wird in der Bitmap so angezeigt, wie es zum Zeitpunkt der letzten Speicherung der Arbeitsmappe angezeigt wurde, einschließlich aller vom Steuerelement angezeigten Daten. Weitere Informationen zu dem ActiveX-Steuerelement, das Windows Forms Steuerelemente und Bitmaps enthält, finden Sie unter [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 Unter bestimmten Bedingungen wird der Code nicht geladen und wird nur die Bitmap angezeigt, beispielsweise wenn der Benutzer die Arbeitsmappe im Entwurfsmodus öffnet. Außerdem kann, wenn der Benutzer die Arbeitsmappe auf einem Computer öffnet, auf dem [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nicht installiert ist, die Anpassung nicht ausgeführt werden, sodass die Steuerelemente nicht geladen werden können und daher nur die Bitmap des Steuerelements sichtbar ist. Sie sollten persönliche Informationen stets aus Steuerelementen in einer Arbeitsmappe entfernen, bevor Sie die Arbeitsmappe speichern und an andere Benutzer senden. So ist sichergestellt, dass Sie vertrauliche Informationen nicht versehentlich preisgeben.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Abgleichen der Steuerelement Größe mit der Zellgröße auf einem Excel-Arbeitsblatt
 Sie können ein Steuerelement so konfigurieren, dass dessen Größe automatisch bei Änderung der Größe der übergeordneten Zelle geändert wird. Weitere Informationen finden Sie unter Gewusst [wie: Ändern der Größe von Steuerelementen innerhalb von Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Komponenten hinzufügen, die von allen Arbeitsblättern gemeinsam genutzt werden
 Sie können Komponenten, die auf allen Arbeitsblättern nutzbar sein sollen (etwa ein <xref:System.Data.DataSet>), dem Arbeitsmappen-Designer hinzufügen, statt sie den Arbeitsblättern hinzuzufügen. Die Komponente wird auf der Komponentenleiste angezeigt.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formel zum Einbetten von Steuerelementen in einem Excel-Arbeitsblatt
 Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

### <a name="layout-style-of-controls-on-a-word-document"></a>Layoutstil von Steuerelementen in einem Word-Dokument
 Wenn Sie einem Word-Dokument in einem Projekt auf Dokumentebene mithilfe des Visual Studio Designers ein Steuerelement hinzufügen, wird das Steuerelement in den Textfluss eingefügt. Um den Layoutstil eines Steuerelements zu ändern, klicken Sie mit der rechten Maustaste auf das Steuerelement, und klicken Sie dann auf **Steuerelement formatieren**. Wählen Sie im Dialogfeld **Objekt formatieren** auf der Seite **Layout** eine Umbruchart aus.

 Wenn Sie einem Word-Dokument zur Laufzeit ein Steuerelement hinzufügen, können Sie die layoutart des neuen Steuer Elements angeben, indem Sie verschiedene `Add` \<*control class*> Methoden Überladungen der- <xref:Microsoft.Office.Tools.Word.ControlCollection> Klasse verwenden:

- Um ein Steuerelement in den Textfluss einzufügen, verwenden Sie eine Überladung, die einen Bereich ( <xref:Microsoft.Office.Interop.Word.Range> ) akzeptiert, der die Position des Steuerelements angibt.

- Um ein Steuerelement als unverankerte Form einzufügen, verwenden Sie eine Überladung, die die linke und die obere Koordinate des Steuerelements akzeptiert.

  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Wenn Sie eine Word-Vorlage im Visual Studio-Designer öffnen, sind nicht ausgerichtete Steuerelemente in der Vorlage möglicherweise nicht sichtbar, da Visual Studio die Vorlage in der Ansicht **Normal** öffnet. Damit die Steuerelemente angezeigt werden, ändern Sie die Ansicht in **Seitenlayout**.

### <a name="controls-outside-the-main-document-body"></a>Steuerelemente außerhalb des Hauptdokument Texts
 Windows Forms-Steuerelemente werden in Kopf- oder Fußzeilen oder in einem Unterdokument nicht unterstützt.

### <a name="add-components-at-design-time"></a>Hinzufügen von Komponenten zur Entwurfszeit
 Bestimmte Steuerelemente oder Komponenten sind auf einem Dokument nicht sichtbar, sondern werden stattdessen auf einer Komponentenleiste angezeigt. Visual Studio stellt eine Komponentenleiste für jedes Dokumentfenster bereit. Die Komponentenleiste wird nur dann auf dem Bildschirm angezeigt, wenn Komponenten auf dem jeweiligen Dokument vorhanden sind.

## <a name="see-also"></a>Weitere Informationen
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Exemplarische Vorgehensweise: Ändern der Arbeitsblatt Formatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Exemplarische Vorgehensweise: Ändern der Dokument Formatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Einschränkungen für Windows Forms Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Options Feldern](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Options Feldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
