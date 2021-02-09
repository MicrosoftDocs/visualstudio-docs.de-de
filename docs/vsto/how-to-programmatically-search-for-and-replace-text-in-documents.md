---
title: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Text in einem Microsoft Word-Dokument Programm gesteuert zu suchen und zu ersetzen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3ef1a32d145169db815915ee93d03893943e71f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877901"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Gewusst wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten
  Das <xref:Microsoft.Office.Interop.Word.Find>-Objekt ist ein Element des <xref:Microsoft.Office.Interop.Word.Selection>- und des <xref:Microsoft.Office.Interop.Word.Range>-Objekts, und Sie können eines dieser Objekte verwenden, um in Microsoft Office Word-Dokumenten nach Text zu suchen. Der Befehl "Ersetzen" ist eine Erweiterung des Befehls "Suchen".

 Verwenden Sie ein <xref:Microsoft.Office.Interop.Word.Find>-Objekt, um ein Microsoft Office Word-Dokument in einer Schleife zu durchlaufen und nach bestimmtem Text, einer Formatierung oder einem Stil zu suchen. Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A>, um gefundene Elemente zu ersetzen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Verwenden eines Auswahl Objekts
 Wenn Sie ein <xref:Microsoft.Office.Interop.Word.Selection>-Objekt zum Suchen nach Text verwenden, gelten die von Ihnen angegebenen Suchkriterien nur für den zurzeit markierten Text. Wenn die <xref:Microsoft.Office.Interop.Word.Selection> eine Einfügemarke ist, wird das Dokument durchsucht. Wenn ein Element gefunden wird, das mit die Suchkriterien übereinstimmt, wird es automatisch ausgewählt.

 Sie müssen unbedingt beachten, dass die <xref:Microsoft.Office.Interop.Word.Find>-Kriterien kumulativ sind. Dies bedeutet, dass Kriterien früheren Suchkriterien hinzugefügt werden. Deaktivieren Sie alle Formatierungen aus vorherigen Suchvorgängen mithilfe der Methode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, bevor Sie den Suchvorgang ausführen.

### <a name="to-find-text-using-a-selection-object"></a>So suchen mit einem Selection-Objekt nach Text

1. Weisen Sie einer Variablen eine Suchzeichenfolge zu.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Löschen Sie die Formatierung aus vorherigen Suchvorgängen.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Führen Sie die Suche aus, und zeigen Sie ein Meldungsfeld mit den Ergebnissen an.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   Das folgende Beispiel zeigt die vollständige Methode.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Verwenden eines Range-Objekts
 Mit einem <xref:Microsoft.Office.Interop.Word.Range>-Objekt können Sie nach Text suchen, ohne dass eine Anzeige in der Benutzeroberfläche erfolgt. Das <xref:Microsoft.Office.Interop.Word.Find> -Objekt gibt **true** zurück, wenn der Text gefunden wird, der den Suchkriterien entspricht, und **false** , wenn dies nicht der Fall ist. Es definiert außerdem das <xref:Microsoft.Office.Interop.Word.Range>-Objekt so neu, dass es den Suchkriterien entspricht, wenn der Text gefunden wird.

### <a name="to-find-text-using-a-range-object"></a>So suchen Sie mithilfe eines Range-Objekts nach Text

1. Definieren Sie ein <xref:Microsoft.Office.Interop.Word.Range>-Objekt, das aus dem zweiten Absatz im Dokuments besteht.

    Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. Wenn Sie die- <xref:Microsoft.Office.Interop.Word.Range.Find%2A> Eigenschaft des- <xref:Microsoft.Office.Interop.Word.Range> Objekts verwenden, löschen Sie zunächst alle vorhandenen Formatierungsoptionen, und suchen Sie dann nach der Zeichenfolge **Find Me**.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Zeigen Sie die Ergebnisse der Suche in einem Meldungsfeld an, und wählen Sie den <xref:Microsoft.Office.Interop.Word.Range> aus, um sie sichtbar zu machen.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Wenn bei der Suche ein Fehler auftritt, wird der zweite Absatz ausgewählt. Wenn die Suche erfolgreich ist, werden die Suchkriterien angezeigt.

   Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisDocument` -Klasse im Projekt aus.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   Das folgende Beispiel zeigt den vollständigen Code für ein VSTO-Add-In. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Suchen nach und Ersetzen von Text in Dokumenten
 Der folgende Code durchsucht die aktuelle Auswahl und ersetzt alle Vorkommen der Zeichenfolge **Find Me** durch die **gefundene** Zeichenfolge.

### <a name="to-search-for-and-replace-text-in-documents"></a>So suchen Sie nach Text und ersetzen Text in Dokumenten

1. Fügen Sie den folgenden Beispielcode der Klasse `ThisDocument` oder `ThisAddIn` im Projekt hinzu.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     Die Klasse <xref:Microsoft.Office.Interop.Word.Find> verfügt über eine Methode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, und die Klasse <xref:Microsoft.Office.Interop.Word.Replacement> verfügt ebenfalls über eine eigene Methode <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Wenn Sie Such-und Ersetzungs Vorgänge ausführen, müssen Sie die clearformatierung-Methode beider-Objekte verwenden. Wenn Sie nur das <xref:Microsoft.Office.Interop.Word.Find>-Objekt verwenden, erhalten Sie ggf. unerwartete Ergebnisse im Ersetzungstext.

2. Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> des <xref:Microsoft.Office.Interop.Word.Find>-Objekts, um jedes gefundene Element zu ersetzen. Verwenden Sie zum Angeben der zu ersetzenden Elemente den *Replace* -Parameter. Dieser Parameter kann einen der folgenden <xref:Microsoft.Office.Interop.Word.WdReplace>-Werte aufweisen:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> ersetzt alle gefundenen Elemente.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> ersetzt keines der gefundenen Elemente.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> ersetzt das erste gefundene Element.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Gewusst wie: Programm gesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Wiederherstellen der Auswahl nach Such Vorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
