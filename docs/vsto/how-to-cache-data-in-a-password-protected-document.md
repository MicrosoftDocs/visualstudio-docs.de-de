---
title: 'Vorgehensweise: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument'
description: Wenn Sie dem Daten Cache in einem Dokument oder einer Arbeitsmappe, die mit einem Kennwort geschützt ist, Daten hinzufügen, können Sie Änderungen an den zwischengespeicherten Daten speichern, indem Sie zwei Methoden in Ihrem Projekt überschreiben.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a11b70da4bdd2500f70d2b45f025340af21ea94
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845998"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Vorgehensweise: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument
  Wenn Sie dem Daten Cache in einem Dokument oder einer Arbeitsmappe, das mit einem Kennwort geschützt ist, Daten hinzufügen, werden Änderungen an den zwischengespeicherten Daten nicht automatisch gespeichert. Sie können Änderungen an den zwischengespeicherten Daten speichern, indem Sie zwei Methoden in Ihrem Projekt überschreiben.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Zwischenspeichern in Word-Dokumenten

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>So speichern Sie Daten in einem Word-Dokument, das mit einem Kennwort geschützt ist

1. Markieren Sie in der- `ThisDocument` Klasse ein öffentliches Feld oder eine Eigenschaft, das zwischengespeichert werden soll. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

2. Überschreiben Sie die <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> -Methode in der `ThisDocument` -Klasse, und entfernen Sie den Schutz des Dokuments.

     Wenn das Dokument gespeichert wird, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode auf, um Ihnen die Möglichkeit zu geben, den Schutz des Dokuments aufzuheben. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden.

3. Überschreiben <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> Sie die-Methode in der `ThisDocument` -Klasse und wenden Sie den Schutz erneut auf das Dokument an

     Nachdem das Dokument gespeichert wurde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode auf, um Ihnen die Möglichkeit zu geben, den Schutz erneut auf das Dokument anzuwenden.

### <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht das Zwischenspeichern von Daten in einem Word-Dokument, das mit einem Kennwort geschützt ist. Bevor der Code den Schutz in der <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> Methode entfernt, wird der aktuelle <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> Wert gespeichert, sodass derselbe Schutztyp in der Methode erneut angewendet werden kann <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Kompilieren des Codes
 Fügen Sie diesen Code der- `ThisDocument` Klasse in Ihrem Projekt hinzu. Dieser Code setzt voraus, dass das Kennwort in einem Feld mit dem Namen gespeichert wird `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Zwischenspeichern in Excel-Arbeitsmappen
 In Excel-Projekten ist dieses Verfahren nur erforderlich, wenn Sie die gesamte Arbeitsmappe mit einem Kennwort schützen, indem Sie die- <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> Methode verwenden. Dieses Verfahren ist nicht erforderlich, wenn Sie nur ein bestimmtes Arbeitsblatt mit einem Kennwort schützen, indem Sie die- <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> Methode verwenden.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>So speichern Sie Daten in einer Excel-Arbeitsmappe, die mit einem Kennwort geschützt ist

1. Markieren Sie in der- `ThisWorkbook` Klasse oder einer der `Sheet` *n* -Klassen ein öffentliches Feld oder eine Eigenschaft, das zwischengespeichert werden soll. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

2. Überschreiben Sie die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> -Methode in der `ThisWorkbook` -Klasse, und entfernen Sie den Schutz von der Arbeitsmappe

     Wenn die Arbeitsmappe gespeichert wird, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode auf, um Ihnen die Möglichkeit zu geben, den Schutz für die Arbeitsmappe aufzuheben. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden.

3. Überschreiben <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> Sie die-Methode in der `ThisWorkbook` -Klasse und wenden Sie den Schutz erneut auf das Dokument an

     Nachdem die Arbeitsmappe gespeichert wurde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode auf, um Ihnen die Möglichkeit zu geben, den Schutz auf die Arbeitsmappe erneut anzuwenden.

### <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Daten in einer Excel-Arbeitsmappe zwischengespeichert werden, die mit einem Kennwort geschützt ist. Bevor der Code den Schutz in der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> Methode entfernt, speichert er die aktuellen <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> -und- <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> Werte, sodass derselbe Schutztyp in der-Methode erneut angewendet werden kann <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Kompilieren des Codes
 Fügen Sie diesen Code der- `ThisWorkbook` Klasse in Ihrem Projekt hinzu. Dieser Code setzt voraus, dass das Kennwort in einem Feld mit dem Namen gespeichert wird `securelyStoredPassword` .

## <a name="see-also"></a>Siehe auch
- [Daten zwischenspeichern](../vsto/caching-data.md)
- [Gewusst wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Vorgehensweise: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
