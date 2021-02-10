---
title: 'Gewusst wie: Programm gesteuertes Speichern von Dokumenten'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um ein Dokument Programm gesteuert zu speichern, ohne den Namen des Dokuments oder einen neuen Namen zu ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 34992bb4f76f68229bebbdb98265838f049dc288
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949778"
---
# <a name="how-to-programmatically-save-documents"></a>Gewusst wie: Programm gesteuertes Speichern von Dokumenten

Es gibt mehrere Möglichkeiten, Microsoft Office Word-Dokumente zu speichern. Sie können ein Dokument speichern, ohne den Namen des Dokuments zu ändern, oder Sie können ein Dokument mit einem neuen Namen speichern.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Speichern eines Dokuments, ohne den Namen zu ändern

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>So speichern Sie das Dokument, das einer Anpassung auf Dokument Ebene zugeordnet ist

1. Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.Save%2A> -Methode der <xref:Microsoft.Office.Tools.Word.Document> -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>So speichern Sie das aktive Dokument

1. Ruft die- <xref:Microsoft.Office.Interop.Word._Document.Save%2A> Methode für das aktive Dokument auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Wenn Sie nicht sicher sind, ob das Dokument, das Sie speichern möchten, das aktive Dokument ist, können Sie anhand seines Namens darauf verweisen.

### <a name="to-save-a-document-specified-by-name"></a>So speichern Sie ein Dokument, das anhand des Namens angegeben ist

1. Verwenden Sie den Dokumentnamen als Argument für die Auflistung <xref:Microsoft.Office.Interop.Word.Documents> . Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Speichern eines Dokuments unter einem neuen Namen

Verwenden Sie die- `SaveAs` Methode, um ein Dokument mit einem neuen Namen zu speichern. Sie können diese Methode des- <xref:Microsoft.Office.Tools.Word.Document> Host Elements in einem Word-Projekt auf Dokument Ebene oder einem systemeigenen- <xref:Microsoft.Office.Interop.Word.Document> Objekt in einem beliebigen Word-Projekt verwenden. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben, aber andere Argumente sind optional.

> [!NOTE]
> Wenn Sie das Dialogfeld " **SaveAs** " innerhalb des <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> -Ereignis Handlers von anzeigen `ThisDocument` und den *Cancel* -Parameter auf " **false**" festlegen, kann die Anwendung unerwartet beendet werden. Wenn Sie den *Cancel* -Parameter auf **true** festlegen, wird eine Fehlermeldung mit dem Hinweis angezeigt, dass die automatische Speicherung deaktiviert wurde.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>So speichern Sie das Dokument, das einer Anpassung auf Dokument Ebene zugeordnet ist, mit einem neuen Namen

1. `SaveAs`Verwenden Sie die-Methode der- `ThisDocument` Klasse in Ihrem Projekt, und verwenden Sie dabei einen voll qualifizierten Pfad und Dateinamen. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument` -Klasse aus.

    > [!NOTE]
    > Die- `SaveAs` Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder wenn andere Probleme beim Speichern einer Datei auftreten. Es empfiehlt sich, einen- `try...catch` Block um die- `SaveAs` Methode oder innerhalb einer aufrufenden Methode zu verwenden.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>So speichern Sie ein System eigenes Dokument mit einem neuen Namen

1. <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>Verwenden Sie die-Methode des, <xref:Microsoft.Office.Interop.Word.Document> das Sie speichern möchten, und verwenden Sie dabei einen voll qualifizierten Pfad und Dateinamen. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.

     Im folgenden Codebeispiel wird das aktive Dokument mit einem neuen Namen gespeichert. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

    > [!NOTE]
    > Die- <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder wenn andere Probleme beim Speichern einer Datei auftreten. Es wird empfohlen, einen **try... Catch** -Block um die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode oder innerhalb einer aufrufenden Methode.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Kompilieren des Codes

Für dieses Codebeispiel benötigen Sie Folgendes:

- Zum Speichern eines Dokuments anhand des Namens muss ein Dokument mit dem Namen *NewDocument.doc* in einem Verzeichnis mit dem Namen *Test* auf Laufwerk C vorhanden sein.

- Um ein Dokument mit einem neuen Namen zu speichern, muss ein Verzeichnis mit dem Namen " *Test* " auf Laufwerk "C" vorhanden sein.

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Programm gesteuertes schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)
- [Gewusst wie: Programm gesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)
- [Dokument Host Element](../vsto/document-host-item.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
