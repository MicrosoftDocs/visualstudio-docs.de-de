---
title: 'Gewusst wie: Programm gesteuertes Aktualisieren von Lesezeichen Text'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Einfügen von Text in ein Platzhalter-Lesezeichen in einem Microsoft Word-Dokument verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b9fa4b5ef19fdcaae38ef477952580f6568fcc0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523552"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Gewusst wie: Programm gesteuertes Aktualisieren von Lesezeichen Text
  Sie können Text in ein Platzhalterlesezeichen in einem Microsoft Office Word-Dokument einfügen, um den Text zu einem späteren Zeitpunkt abzurufen oder Text in einem Lesezeichen zu ersetzen. Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie auch Text in einem an Daten gebundenen <xref:Microsoft.Office.Tools.Word.Bookmark>-Steuerelement aktualisieren. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Das Lesezeichenobjekt kann einem von zwei Typen entsprechen:

- Einem <xref:Microsoft.Office.Tools.Word.Bookmark>-Hoststeuerelement.

   <xref:Microsoft.Office.Tools.Word.Bookmark>-Steuerelemente erweitern systemeigene <xref:Microsoft.Office.Interop.Word.Bookmark>-Objekte, indem sie die Datenbindung aktivieren und Ereignisse verfügbar machen. Weitere Informationen zu Host Steuerelementen finden Sie unter [Übersicht über Host Elemente und Host](../vsto/host-items-and-host-controls-overview.md)Steuerelemente.

- Ein systemeigenes <xref:Microsoft.Office.Interop.Word.Bookmark>-Objekt.

   <xref:Microsoft.Office.Interop.Word.Bookmark>-Objekte verfügen über keine Ereignisse oder Datenbindungsfunktionen.

  Wenn Sie einem Lesezeichen Text zuordnen, unterscheidet sich das Verhalten zwischen <xref:Microsoft.Office.Interop.Word.Bookmark> und <xref:Microsoft.Office.Tools.Word.Bookmark>. Weitere Informationen finden Sie unter [Bookmark Control](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Verwenden von Host Steuerelementen

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>So aktualisieren Lesezeicheninhalte mithilfe des Lesezeichen-Steuerelements

1. Erstellen Sie eine Prozedur, die ein `bookmark`-Argument für den Namen des Lesezeichens akzeptiert, und ein`newText`-Argument für die Zeichenfolge zum Zuweisen der <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>-Eigenschaft.

    > [!NOTE]
    > Die Zuweisung von Text zu den Eigenschaften <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> oder <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> eines <xref:Microsoft.Office.Tools.Word.Bookmark>-Steuerelements führt nicht dazu, dass das Lesezeichen gelöscht wird.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Weisen Sie die *Newtext* -Zeichenfolge der- <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> Eigenschaft von zu <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Verwenden von Word-Objekten

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>So aktualisieren Lesezeicheninhalte mithilfe eines Word-Lesezeichenobjekts

1. Erstellen Sie eine Prozedur, die ein `bookmark`-Argument für den Namen von <xref:Microsoft.Office.Interop.Word.Bookmark> und ein `newText`-Argument für die Zeichenfolge zur Zuweisung zur <xref:Microsoft.Office.Interop.Word.Range.Text%2A>-Eigenschaft des Lesezeichens enthält.

    > [!NOTE]
    > Die Zuweisung von Text zu einem systemeigenen Word-<xref:Microsoft.Office.Interop.Word.Bookmark>-Objekt führt nicht dazu, dass das Lesezeichen gelöscht wird.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Weisen Sie die *Newtext* -Zeichenfolge der- <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Eigenschaft des Lesezeichens zu, wodurch das Lesezeichen automatisch gelöscht wird. Fügen Sie das Lesezeichen der <xref:Microsoft.Office.Interop.Word.Bookmarks>-Auflistung dann erneut hinzu.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Bookmark-Steuerelement](../vsto/bookmark-control.md)
