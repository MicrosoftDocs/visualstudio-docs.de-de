---
title: 'Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Dokumenten'
description: Um zu erfahren, wie Sie die Rechtschreibung in einem Dokument Programm gesteuert überprüfen können, können Sie die CheckSpelling-Methode verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85294b21e9fd1f52f5cc707fc6824a87530e3cda
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848312"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Gewusst wie: Programm gesteuertes Überprüfen der Rechtschreibung in Dokumenten
  Verwenden Sie die-Methode, um die Rechtschreibung in einem Dokument zu überprüfen <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> . Diese Methode gibt einen booleschen Wert zurück, der angibt, ob der angegebene Parameter korrekt geschrieben ist.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>So überprüfen Sie die Rechtschreibung und anzeigen Ergebnisse in einem Meldungs Feld

1. Ruft die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> -Methode auf und übergibt ihr einen Textbereich, der auf Rechtschreibfehler überprüft werden soll. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
