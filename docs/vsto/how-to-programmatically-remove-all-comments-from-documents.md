---
title: 'Gewusst wie: Programm gesteuertes Entfernen aller Kommentare aus Dokumenten'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um alle Kommentare Programm gesteuert aus einem Microsoft Word-Dokument zu entfernen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8cb4e2e8fe51dfe6596f58470c714e8ef2412d46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968865"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Gewusst wie: Programm gesteuertes Entfernen aller Kommentare aus Dokumenten
  Verwenden Sie die `DeleteAllComments`-Methode, um alle Kommentare aus einem Microsoft Office Word-Dokument zu entfernen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>So entfernen Sie alle Kommentare aus einem Dokument, das Teil einer Anpassung auf Dokumentebene ist

1. Rufen Sie in Ihrem Projekt die <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> -Methode der `ThisDocument` -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument` -Klasse aus.

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>So entfernen Sie alle Kommentare aus einem Dokument mithilfe eines VSTO-Add-ins

1. Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> -Methode der <xref:Microsoft.Office.Interop.Word.Document> auf, aus der Sie Kommentare entfernen möchten.

     Das folgende Codebeispiel entfernt alle Kommentare aus dem aktiven Dokument. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Dokument Host Element](../vsto/document-host-item.md)
