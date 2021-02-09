---
title: 'Gewusst wie: Programm gesteuertes Festlegen von Suchoptionen in Word'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Suchoptionen für die Auswahl in Microsoft Word Programm gesteuert festzulegen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e583b7deb9fbe37f40e582d2c8a946332dd00ffa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913463"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Gewusst wie: Programm gesteuertes Festlegen von Suchoptionen in Word
  Es gibt zwei Möglichkeiten, Suchoptionen für die Auswahl in Microsoft Office Word-Dokumenten festzulegen:

- Legen Sie einzelne Eigenschaften eines- <xref:Microsoft.Office.Interop.Word.Find> Objekts fest.

- Verwenden Sie Argumente der- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode eines- <xref:Microsoft.Office.Interop.Word.Find> Objekts.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Verwenden von Eigenschaften eines Find-Objekts
 Der folgende Code legt die Eigenschaften eines- <xref:Microsoft.Office.Interop.Word.Find> Objekts fest, um nach Text innerhalb der aktuellen Auswahl zu suchen. Beachten Sie, dass die Suchkriterien, z. b. die Suche nach vorne, Wrapping und Text, nach denen gesucht werden soll, Eigenschaften des- <xref:Microsoft.Office.Interop.Word.Find> Objekts sind.

 Das Festlegen der Eigenschaften des- <xref:Microsoft.Office.Interop.Word.Find> Objekts ist nicht hilfreich, wenn Sie c#-Code schreiben, da Sie dieselben Eigenschaften wie Parameter in der- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode angeben müssen. Daher enthält dieses Beispiel nur Visual Basic-Code.

### <a name="to-set-search-options-using-a-find-object"></a>So legen Sie Suchoptionen mithilfe eines Find-Objekts fest

1. Legen Sie die Eigenschaften eines- <xref:Microsoft.Office.Interop.Word.Find> Objekts fest, um eine Auswahl für die **Textsuche** zu suchen.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Verwenden von Execute-Methoden Argumenten
 Im folgenden Code wird die- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode eines- <xref:Microsoft.Office.Interop.Word.Find> Objekts verwendet, um nach Text innerhalb der aktuellen Auswahl zu suchen. Beachten Sie, dass die Suchkriterien, z. b. die Suche nach vorne, Wrapping und Text, nach denen gesucht werden soll, als Parameter der-Methode weitergegeben werden <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

### <a name="to-set-search-options-using-execute-method-arguments"></a>So legen Sie Suchoptionen mithilfe von Execute-Methoden Argumenten fest

1. Übergeben Sie Suchkriterien als Parameter der- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode, um durch eine Auswahl für die Textsuche nach vorne zu suchen. 

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Gewusst wie: Programm gesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Gewusst wie: Programm gesteuertes Wiederherstellen der Auswahl nach Such Vorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)
