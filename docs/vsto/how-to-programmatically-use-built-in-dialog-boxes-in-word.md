---
title: 'Gewusst wie: Programm gesteuertes Verwenden integrierter Dialogfelder in Word'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um integrierte Dialogfelder in Microsoft Word Programm gesteuert zu verwenden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 18a6176c6472f1587e00364f0e0bd300611eabf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897521"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Gewusst wie: Programm gesteuertes Verwenden integrierter Dialogfelder in Word
  Wenn Sie mit Microsoft Office Word arbeiten, gibt es Zeiten, in denen Sie Dialogfelder für Benutzereingaben anzeigen müssen. Obwohl Sie eigene erstellen können, sollten Sie auch die integrierten Dialogfelder in Word verwenden, die in der-Auflistung des-Objekts verfügbar gemacht werden <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> . Dies ermöglicht Ihnen den Zugriff auf über 200 der integrierten Dialogfelder, die als Enumerationen dargestellt werden.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Anzeigen von Dialogfeldern
 Um ein Dialogfeld anzuzeigen, verwenden Sie einen der Werte der- <xref:Microsoft.Office.Interop.Word.WdWordDialog> Enumeration, um ein-Objekt zu erstellen <xref:Microsoft.Office.Interop.Word.Dialog> , das das Dialogfeld darstellt, das Sie anzeigen möchten. Anschließend wird die- <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> Methode des- <xref:Microsoft.Office.Interop.Word.Dialog> Objekts aufgerufen.

 Im folgenden Codebeispiel wird veranschaulicht, wie das Dialogfeld zum **Öffnen von Dateien** angezeigt wird. Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder der- `ThisAddIn` Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Zugreifen auf Dialogfeld Elemente, die durch späte Bindung verfügbar sind
 Einige Eigenschaften und Methoden von Dialogfeldern in Word sind nur über die späte Bindung verfügbar. In Visual Basic Projekten, in denen **Option Strict aktiviert** ist, müssen Sie die Reflektion verwenden, um auf diese Member zuzugreifen. Weitere Informationen finden Sie unter [späte Bindung in Office](../vsto/late-binding-in-office-solutions.md)-Projektmappen.

 Im folgenden Codebeispiel wird veranschaulicht, wie die **Name** -Eigenschaft des Dialog Felds zum **Öffnen von Dateien** in Visual Basic Projekten verwendet wird, in denen **Option Strict** deaktiviert ist oder in Visual c#-Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder abzielen [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder der- `ThisAddIn` Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Im folgenden Codebeispiel wird veranschaulicht, wie mithilfe von Reflektion auf die **Name** -Eigenschaft des Dialog Felds zum **Öffnen von Dateien** in Visual Basic-Projekte zugegriffen werden kann, in denen **Option Strict aktiviert** ist. Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder der- `ThisAddIn` Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
