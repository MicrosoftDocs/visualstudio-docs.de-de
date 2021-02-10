---
title: 'Gewusst wie: Programm gesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Verwenden von Microsoft Word-Dialogfeldern im ausgeblendeten Modus verwenden können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0977e7241920ad23a6248bb2349ddaeb10a5e931
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931239"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Gewusst wie: Programm gesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus
  Sie können komplexe Vorgänge mit einem Methodenaufruf ausführen, indem Sie die integrierten Dialogfelder in Microsoft Office Word aufrufen, ohne Sie dem Benutzer anzuzeigen. Verwenden Sie hierzu die- <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> Methode des-Objekts, <xref:Microsoft.Office.Interop.Word.Dialog> ohne die-Methode aufrufen zu müssen <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Beispiele
 In den folgenden Codebeispielen wird veranschaulicht, wie das Dialogfeld **Seite einrichten** im Modus ausgeblendet verwendet wird, um mehrere Seiten Einrichtungs Eigenschaften ohne Benutzereingaben festzulegen. In den Beispielen wird ein- <xref:Microsoft.Office.Interop.Word.Dialog> Objekt verwendet, um eine benutzerdefinierte Seitengröße zu konfigurieren. Die spezifischen Einstellungen für das Einrichten der Seite, z. b. der obere Rand, der untere Rand usw., sind als spät gebundene Eigenschaften des- <xref:Microsoft.Office.Interop.Word.Dialog> Objekts verfügbar. Diese Eigenschaften werden von Word zur Laufzeit dynamisch erstellt.

 Im folgenden Beispiel wird veranschaulicht, wie diese Aufgabe in Visual Basic Projekten durchgeführt wird, bei denen **Option Strict** deaktiviert ist, und in Visual c#-Projekten, die auf ausgerichtet sind [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In diesen Projekten können Sie Features für die späte Bindung in den Visual Basic-und Visual c#-Compilern verwenden. Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder der- `ThisAddIn` Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Im folgenden Beispiel wird veranschaulicht, wie diese Aufgabe in Visual Basic Projekten durchgeführt wird, in denen **Option Strict aktiviert** ist. In diesen Projekten müssen Sie die Reflektion verwenden, um auf die spät gebundenen Eigenschaften zuzugreifen. Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder der- `ThisAddIn` Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Verwenden integrierter Dialogfelder in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
- [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
