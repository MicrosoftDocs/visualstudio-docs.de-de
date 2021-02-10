---
title: 'Gewusst wie: Programm gesteuertes durchlaufen gefundener Elemente in Dokumenten'
description: Erfahren Sie, wie Sie mithilfe von Visual Studio gefundene Elemente in einem Microsoft Word-Dokument Programm gesteuert durchlaufen können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a447b0fd2651ceafd789de084c56e0cea03a69e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934831"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Gewusst wie: Programm gesteuertes durchlaufen gefundener Elemente in Dokumenten
  Die <xref:Microsoft.Office.Interop.Word.Find> -Klasse hat eine <xref:Microsoft.Office.Interop.Word.Find.Found%2A> -Eigenschaft, die jedes Mal **true** zurückgibt, wenn ein gesuchtes Element gefunden wurde. Sie können alle in einem <xref:Microsoft.Office.Interop.Word.Range> -Objekt gefundenen Instanzen mit der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> -Methode durchlaufen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>So durchlaufen Sie gefundene Elemente

1. Deklarieren Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt.

    Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Find.Found%2A> -Eigenschaft in einer Schleife, um nach allen Vorkommen der Zeichenfolge im Dokument zu suchen, und erhöhen Sie eine ganzzahlige Variable jedes Mal um 1, wenn die Zeichenfolge gefunden wurde.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. Zeigen Sie in einem Meldungsfeld an, wie oft die Zeichenfolge gefunden wurde.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   Die folgenden Beispiele zeigen die vollständige Methode.

## <a name="document-level-customization-example"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="to-loop-through-items-in-a-document-level-customization"></a>So durchlaufen Sie Elemente in einer Anpassung auf Dokumentebene

1. Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>So durchlaufen Sie Elemente in einem VSTO-Add-in

1. Das folgende Beispiel zeigt den vollständigen Code für ein VSTO-Add-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Gewusst wie: Programm gesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Wiederherstellen der Auswahl nach Such Vorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
