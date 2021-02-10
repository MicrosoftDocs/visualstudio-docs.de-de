---
title: 'Gewusst wie: Programm gesteuertes Drucken von Visio-Dokumenten'
description: Erfahren Sie, wie Sie ein vollständiges Microsoft Visio-Dokument drucken oder nur eine bestimmte Seite in diesem Dokument drucken können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df2cd5137f05caaf7b8437fb2d903aeecc7d3e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933036"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Gewusst wie: Programm gesteuertes Drucken von Visio-Dokumenten
  Sie können ein vollständiges Microsoft Office Visio-Dokument oder nur eine bestimmte Seite drucken.

 Ausführliche Informationen zu den Druckmethoden finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) -Methode und [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) -Methode.

## <a name="print-a-visio-document"></a>Drucken eines Visio-Dokuments

### <a name="to-print-a-complete-document"></a>So drucken Sie ein vollständiges Dokument

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Print` -Methode des `Microsoft.Office.Interop.Visio.Document` -Objekts auf, das Sie drucken möchten.

     Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Drucken einer Seite eines Visio-Dokuments

### <a name="to-print-a-page-of-a-document"></a>So drucken Sie eine Seite eines Dokuments

- Rufen Sie die `Microsoft.Office.Interop.Visio.Pages.Print` -Methode des `Microsoft.Office.Interop.Visio.Pages` -Objekts auf, das Sie drucken möchten.

     Im folgenden Codebeispiel wird die erste Seite des aktiven Dokuments gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Gewusst wie: Programm gesteuertes schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
