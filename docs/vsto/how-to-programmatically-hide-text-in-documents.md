---
title: 'Gewusst wie: Programm gesteuertes Ausblenden von Text in Dokumenten'
description: Erfahren Sie, wie Sie Text in einem Microsoft Word-Dokument ausblenden können, indem Sie die Hidden-Eigenschaft der Schriftart für einen bestimmten Textbereich festlegen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a375e8b844f82b5d310841d7b4cdc092b18ff6c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525704"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Gewusst wie: Programm gesteuertes Ausblenden von Text in Dokumenten
  Sie können Text in einem Dokument ausblenden, indem Sie die <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> -Eigenschaft der <xref:Microsoft.Office.Interop.Word.Range.Font%2A> für einen bestimmten Textbereich festlegen.

 Beispielsweise können Sie den Text in einer <xref:Microsoft.Office.Tools.Word.Bookmark> (in einer Anpassung auf Dokument Ebene) oder <xref:Microsoft.Office.Interop.Word.Bookmark> in einer (in einem VSTO-Add-in) vorübergehend ausblenden, bevor Sie ein Dokument an einen Drucker senden.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>So blenden Sie Text in einem Bookmark-Steuerelement beim Drucken des Dokuments aus

1. Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich ausblendet.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich anzeigt.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Übergeben Sie den Bereich einer Textmarke an die `HideText` -Methode, drucken Sie das Dokument, und übergeben Sie dann denselben Bereich an die `UnhideText` -Methode.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 In diesem Codebeispiel wird davon ausgegangen, dass das Dokument ein- <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement (in einer Anpassung auf Dokument Ebene) oder ein- <xref:Microsoft.Office.Interop.Word.Bookmark> Steuerelement (in einem VSTO-Add-in) mit dem Namen enthält `bookmark1` .

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Gewusst wie: Programm gesteuertes Aktualisieren von Lesezeichen Text](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
