---
title: 'Gewusst wie: Programm gesteuertes Erweitern von Bereichen in Dokumenten'
description: Erfahren Sie, wie Sie Start-und Endpunkt Bereiche in einem Microsoft Word-Dokument auf Dokument-oder Anwendungsebene Programm gesteuert erweitern können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61ed056b5cebcebb6fe2dffd66dc374e4e1f9205
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525737"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Gewusst wie: Programm gesteuertes Erweitern von Bereichen in Dokumenten
  Nachdem Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt in einem Microsoft Office Word-Dokument definiert haben, ändern Sie dessen Start- und Endpunkt mithilfe der Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Die Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> akzeptieren dieselben beiden Argumente *Unit* und *Count*. Die Methoden *Count* -Argument entspricht der Anzahl zu verschiebender Einheiten, und das *Unit* -Argument kann einer der folgenden <xref:Microsoft.Office.Interop.Word.WdUnits> -Werte sein:

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  Im folgenden Beispiel wird ein aus sieben Zeichen bestehender Bereich definiert. Anschließend wird die Startposition des Bereichs von der ursprünglichen Startposition aus um sieben Zeichen verschoben. Da die Endposition des Bereichs ebenfalls sieben Zeichen von der Startposition entfernt war, umfasst der resultierende Bereich 0 Zeichen. Durch den Code wird die Endposition dann von der aktuellen Endposition um sieben Zeichen verschoben.

## <a name="to-extend-a-range"></a>So erweitern Sie einen Bereich

1. Definieren Sie einen Bereich von Zeichen. Weitere Informationen finden Sie unter Gewusst [wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um die Startposition des Bereichs zu verschieben.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um die Endposition des Bereichs zu verschieben.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Anpassungs Code auf Dokument Ebene

### <a name="to-extend-a-range-in-a-document-level-customization"></a>So erweitern Sie einen Bereich in einer Anpassung auf Dokumentebene

1. Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>VSTO-Add-In-Code

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>So erweitern Sie einen Bereich in einem VSTO-Add-In auf Anwendungsebene

1. Das folgende Beispiel zeigt den vollständigen Code für ein VSTO-Add-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Gewusst wie: Programm gesteuertes reduzieren von Bereichen oder Auswahlen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Abrufen von Start-und Endzeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Gewusst wie: Programm gesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
