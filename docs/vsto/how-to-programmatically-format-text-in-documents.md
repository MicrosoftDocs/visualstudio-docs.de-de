---
title: 'Gewusst wie: Programm gesteuertes Formatieren von Text in Dokumenten'
description: Erfahren Sie, wie Sie das Bereichs Objekt verwenden können, um Text in einem Microsoft Word-Dokument Programm gesteuert zu formatieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d5804c7441682a6bedb776558bd2eb5c79605951
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885429"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Gewusst wie: Programm gesteuertes Formatieren von Text in Dokumenten
  Sie können mit dem <xref:Microsoft.Office.Interop.Word.Range> -Objekt Text in einem Microsoft Office Word-Dokument formatieren.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Im folgenden Beispiel wird der erste Absatz des Dokuments markiert, und der Schriftgrad, der Schriftartname und die Ausrichtung werden geändert. Anschließend wird der Bereich markiert und ein Meldungsfeld angezeigt, um die Ausführung des Codes vor dem nächsten Abschnitt zu unterbrechen. Im nächsten Abschnitt wird die Undo-Methode des- <xref:Microsoft.Office.Tools.Word.Document> Host Elements (bei einer Anpassung auf Dokument Ebene) oder die- <xref:Microsoft.Office.Interop.Word.Document> Klasse (für ein VSTO-Add-in) dreimal aufgerufen. Das Format Standardeinzug wird zugewiesen, und ein Meldungsfeld wird angezeigt, um die Codeausführung zu unterbrechen. Anschließend ruft der Code einmal die <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> -Methode auf und zeigt ein Meldungsfeld an.

## <a name="document-level-customization-example"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="to-format-text-using-a-document-level-customization"></a>So formatieren Sie Text mit einer Anpassung auf Dokumentebene

1. Das folgende Beispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In

### <a name="to-format-text-using-a-vsto-add-in"></a>So formatieren Sie Text mithilfe eines VSTO-Add-Ins

1. Das folgende Beispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Gewusst wie: Programm gesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Gewusst wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
