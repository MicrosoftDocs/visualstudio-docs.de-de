---
title: Bookmark-Steuerelement
description: Erfahren Sie, wie das Lesezeichen-Steuerelement ein Lesezeichen ist, das über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53f68bfd9abd26d9dfcb9e253c412a1ddf3c0e28
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848364"
---
# <a name="bookmark-control"></a>Bookmark-Steuerelement
  Das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement ist eine Textmarke, die über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann. Die Textmarke kann als Platzhalter verwendet werden, um ein Element oder eine Position in einem Microsoft Office Word-Dokument zu markieren. Das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement ist eine Kombination aus einem <xref:Microsoft.Office.Interop.Word.Bookmark> - und einem <xref:Microsoft.Office.Interop.Word.Range> -Objekt.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 In Projekten auf Dokumentebene können Sie dem Dokument <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelemente zur Entwurfszeit oder zur Laufzeit hinzufügen. In VSTO-Add-In-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelemente hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement
 Ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement unterstützt die einfache Datenbindung. Die Textmarke sollte mithilfe der <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> -Eigenschaft an eine Datenquelle gebunden werden. Die Standardeigenschaft für die Datenbindung der Textmarke ist die <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> -Eigenschaft.

 Wenn die Daten im gebundenen Dataset aktualisiert werden, zeigt das <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement die Änderungen an.

 In Projekten auf Dokumentebene können Sie Daten auch an Textmarken binden, indem Sie das Fenster **Datenquellen** verwenden. Weitere Informationen finden Sie unter Gewusst [wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formatierung
 Die gesamte auf <xref:Microsoft.Office.Interop.Word.Bookmark> anwendbare Formatierung kann auf ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement angewendet werden. Diese Formatierung schließt Schriftarten, Einzüge, Abstände, Nummerierungen und Stile ein.

## <a name="assign-text-to-the-bookmark"></a>Text dem Lesezeichen zuweisen
 Ein weiterer Unterschied zwischen einem <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> -Objekt und einem <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> -Steuerelement ist das Verhalten beim Zuweisen von Text zur Textmarke. Wenn Sie Text zu einem <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>mit der Länge 0 (null) zuweisen, wird der Text rechts neben der Textmarke angefügt und die Textmarke behält die Länge 0 (null). Wenn Sie jedoch Text zu einem <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>mit der Länge 0 (null) zuweisen, wird der Text in die Textmarke eingefügt und die Länge der Textmarke um die Gesamtzahl der eingefügten Zeichen erweitert.

 Das <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> -Steuerelement verfügt auch über die <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> -Eigenschaft. Diese Eigenschaft unterscheidet sich von der-Eigenschaft, die <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> für die-Eigenschaft eines-Steuer Elements verfügbar ist <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> , oder der- <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> Eigenschaft eines- <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> Objekts.

|Text-Eigenschaft|BESCHREIBUNG|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Verwenden Sie diese Eigenschaft zum Anzeigen von Text in einer Textmarke, und belassen Sie die Textmarke im Dokument. Durch das Zuweisen von Text zur Textmarke wird der Textmarkenbereich erweitert und die Textmarke nicht gelöscht.<br /><br /> `Bookmark1.Text = "Hello world"` fügt z. B. den Text in die Textmarken ein, und die Textmarke bleibt intakt.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Verwenden Sie diese Eigenschaft, um Text an der Position der Textmarke anzuzeigen und die Textmarke automatisch zu löschen. `Bookmark1.Range.Text = "Hello world"` fügt z. B. den Text in die Textmarke ein, und die Textmarke wird gelöscht.|

## <a name="rename-the-control-at-design-time"></a>Umbenennen des Steuer Elements zur Entwurfszeit
 Wenn Sie in Projekten auf Dokumentebene ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement aus der **Toolbox** in Ihr Dokument ziehen, generiert Visual Studio automatisch einen Namen für das Steuerelement. Sie können den Namen des Steuerelemente im Fenster **Eigenschaften** ändern.

## <a name="overlapping-controls"></a>Überlappende Steuerelemente
 Lesezeichen-Steuerelemente können einander überlappen. Der gleiche Text kann von mehr als einem Lesezeichen gemeinsam genutzt werden. Wenn Sie einem der überlappenden Lesezeichen neuen Text zuweisen, enthält dieser nur den neuen Text, und die Lesezeichen überlappen sich nicht mehr. Das andere Lesezeichen enthält jetzt nur den Text, der nicht von den ursprünglich überlappenden Lesezeichen gemeinsam genutzt wurde.

 In der folgenden Tabelle wird gezeigt, wie der Satz „This is sample text.“ wird von zwei überlappenden Lesezeichen gemeinsam genutzt:

|Lesezeichen|Text|
|--------------|----------|
|Überlappende Textmarken|[this is {sample] text.}|
|Bookmark1|This is sample|
|Bookmark2|sample text.|

 Wenn Sie den neuen Text „This is replacement." in bookmark1 zuweisen sind die Lesezeichen nicht überlappend, und Bookmark2 behält nur den Text bei, der ursprünglich nicht Teil von Bookmark1 zuweisen war.

|Lesezeichen|Text|
|--------------|----------|
|Zwei separate Textmarken|[this is replacement]{ text.}|
|Bookmark1|This is replacement|
|Bookmark2|text.|

Wenn Sie den Text eines Lesezeichens ändern, das ein anderes Lesezeichen enthält, wird das innere Lesezeichen nicht gelöscht. Das innere Lesezeichen wird jedoch zu einem leeren Lesezeichen und wechselt zum Ende des äußeren Lesezeichens.

In der folgenden Tabelle wird gezeigt, wie der Satz „This is sample text.“ wird von einem Lesezeichen gemeinsam genutzt, das in einem anderen Lesezeichen enthalten ist:

|Lesezeichen|Text|
|--------------|----------|
|Überlappende Textmarken|[this is {sample} text.]|
|Bookmark1|This is sample text.|
|Bookmark2|Beispiel|

 Wenn Sie den neuen Text „This is replacement." zu Bookmark1 zuweisen, überlappen sich die Textmarken nicht mehr, und Bookmark2 wird zu einer leeren Textmarke, die sich am Ende von Bookmark1 befindet.

|Lesezeichen|Text|
|--------------|----------|
|Zwei separate Textmarken|[Dies ist eine Ersetzung.]{}|
|Bookmark1|This is replacement.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>Ereignisse

Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement verfügbar:

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Siehe auch

- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)