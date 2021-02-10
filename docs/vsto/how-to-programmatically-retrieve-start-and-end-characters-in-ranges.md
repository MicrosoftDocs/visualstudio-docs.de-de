---
title: Programm gesteuertes starten von Start & Endzeichen in Bereichen
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4ff79b916aa0638a03ad51a749856246451eac41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953889"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Gewusst wie: Programm gesteuertes Abrufen von Start-und Endzeichen in Bereichen
  In diesem Beispiel wird veranschaulicht, wie Sie die Zeichenpositionen der Anfangs- und Endposition eines Bereichs abrufen können.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>So rufen Sie Start- und Endzeichen eines Bereichs in einer Anpassung auf Dokumentebene ab

1. Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>So rufen Sie Start-und Endzeichen eines Bereichs mithilfe eines VSTO-Add-Ins ab

1. Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im aktiven Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Gewusst wie: Programm gesteuertes reduzieren von Bereichen oder Auswahlen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Gewusst wie: Programm gesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Gewusst wie: Programm gesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md)
