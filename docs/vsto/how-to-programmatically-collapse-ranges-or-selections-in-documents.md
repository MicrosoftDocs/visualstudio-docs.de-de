---
title: Programm gesteuertes reduzieren von Bereichen oder Auswahlen in Dokumenten
description: Wenn Sie mit einem Bereichs-oder Auswahl Objekt arbeiten, möchten Sie möglicherweise die Auswahl in eine Einfügemarke ändern, bevor Sie Text einfügen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9b063244c8ac611d3a864b9cc3753b5cd8460474
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964289"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Gewusst wie: Programm gesteuertes reduzieren von Bereichen oder Auswahlen in Dokumenten
  Wenn Sie mit einem <xref:Microsoft.Office.Interop.Word.Range> - oder <xref:Microsoft.Office.Interop.Word.Selection> -Objekt arbeiten, möchten Sie die Auswahl vor dem Einfügen von Text möglicherweise auf eine Einfügemarke setzen, um das Überschreiben vorhandenen Texts zu vermeiden. Sowohl das <xref:Microsoft.Office.Interop.Word.Range> -Objekt als auch das- <xref:Microsoft.Office.Interop.Word.Selection> Objekt verfügen über eine Collapse-Methode, die die- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> Enumerationswerte verwendet:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> reduziert die Auswahl auf den Anfang der Auswahl. Dies ist die Standardeinstellung, wenn Sie keinen Enumerationswert angeben möchten.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> reduziert die Auswahl auf das Ende der Auswahl.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>So reduzieren Sie einen Bereich und fügen neuen Text ein

1. Erstellen Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt, das aus dem ersten Absatz des Dokuments besteht.

    Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Verwenden Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> -Enumerationswert, um den Bereich zu reduzieren.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Fügen Sie den neuen Text ein.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Wählen Sie <xref:Microsoft.Office.Interop.Word.Range> aus.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Wenn Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> -Enumerationswert verwenden, wird der Text am Anfang des folgenden Absatzes eingefügt.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Normalerweise würden Sie davon ausgehen, dass ein eingefügter neuer Satz vor der Absatzmarke eingefügt wird. Dies ist jedoch nicht der Fall, weil die Absatzmarke im ursprünglichen Bereich enthalten ist. Weitere Informationen finden Sie unter Gewusst [wie: Programm gesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>So reduzieren Sie einen Bereich in einer Anpassung auf Dokumentebene

1. Das folgende Beispiel zeigt die vollständige Methode für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>So reduzieren Sie einen Bereich in einem VSTO-Add-in

1. Das folgende Beispiel zeigt die Complete-Methode für ein VSTO-Add-in. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Abrufen von Start-und Endzeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Gewusst wie: Programm gesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Gewusst wie: Programm gesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
