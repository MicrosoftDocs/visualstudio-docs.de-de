---
title: 'Gewusst wie: Programm gesteuertes Anzeigen von Dokumenten in der Seitenansicht'
description: Erfahren Sie, wie Sie Dokumente in der Seitenansicht in einem Microsoft Word-Dokument Programm gesteuert anzeigen können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69c5014958d137b534a283b0d07fa048966092be
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525861"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Gewusst wie: Programm gesteuertes Anzeigen von Dokumenten in der Seitenansicht
  Wenn Ihre Projektmappe einen Bericht generiert, können Sie dem Benutzer den Bericht im Seitenansichtsmodus anzeigen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Prozeduren für Anpassungen auf Dokument Ebene

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“-Methode in der Seitenansicht an

1. Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> -Methode der <xref:Microsoft.Office.Tools.Word.Document> -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“-Eigenschaft in der Seitenansicht an

1. Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application> -Objekts auf **true** fest.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Verfahren für VSTO-Add-Ins

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“-Methode in der Seitenansicht an

1. Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts auf, für das Sie eine Vorschau anzeigen möchten. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“-Eigenschaft in der Seitenansicht an

1. Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application> -Objekts auf **true** fest.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)
- [Gewusst wie: Programm gesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)
- [Gewusst wie: Programm gesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)
