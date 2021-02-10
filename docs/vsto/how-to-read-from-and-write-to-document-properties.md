---
title: 'Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Dokumenteigenschaften in Microsoft Excel und Microsoft Word zu erhalten oder festzulegen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 864906e678cb3976e99dd8d9aeb9147e303f2517
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942181"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften
  Sie können Dokumenteigenschaften zusammen mit einem Dokument speichern. Office-Anwendungen stellen eine Reihe integrierter Eigenschaften (z. B. Autor, Titel und Betreff) bereit. In diesem Thema wird gezeigt, wie Dokumenteigenschaften in Microsoft Office Excel und Microsoft Office Word festgelegt werden.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Festlegen von Dokumenteigenschaften in Excel
 Verwenden Sie die folgenden Eigenschaften, um in Excel mit integrierten Eigenschaften zu arbeiten:

- In einem Projekt auf Dokumentebene verwenden Sie die Eigenschaft <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> der Klasse `ThisWorkbook` .

- Verwenden Sie in einem VSTO-Add-In-Projekt die Eigenschaft <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> eines <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekts.

  Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties> -Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty> -Objekten ist. Sie können die Eigenschaft `Item` der Auflistung verwenden, um eine bestimmte Eigenschaft nach Name oder Index in der Auflistung abzurufen.

  Im folgenden Codebeispiel wird veranschaulicht, wie die integrierte Eigenschaft **Revision Number** in einem Projekt auf Dokumentebene geändert wird.

### <a name="to-change-the-revision-number-property-in-excel"></a>So ändern Sie die Eigenschaft "Revisionsnummer" in Excel

1. Weisen Sie die integrierten Eigenschaften einer Variablen zu.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. Inkrementieren Sie die Eigenschaft `Revision Number` um eins.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Festlegen von Dokumenteigenschaften in Word
 Verwenden Sie die folgenden Eigenschaften, um in Word mit integrierten Eigenschaften zu arbeiten:

- In einem Projekt auf Dokumentebene verwenden Sie die Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> der Klasse `ThisDocument` .

- Verwenden Sie in einem VSTO-Add-In-Projekt die Eigenschaft <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> eines <xref:Microsoft.Office.Interop.Word.Document> -Objekts.

  Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties> -Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty> -Objekten ist. Sie können die Eigenschaft `Item` der Auflistung verwenden, um eine bestimmte Eigenschaft nach Name oder Index in der Auflistung abzurufen.

  Im folgenden Codebeispiel wird veranschaulicht, wie die integrierte Eigenschaft **Subject** in einem Projekt auf Dokumentebene geändert wird.

### <a name="to-change-the-subject-property"></a>So ändern Sie die Eigenschaft "Subject"

1. Weisen Sie die integrierten Eigenschaften einer Variablen zu.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. Ändern Sie die Eigenschaft `Subject` in "Whitepaper".

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>Stabile Programmierung
 In den Beispielen wird davon ausgegangen, dass Sie den Code in der Klasse `ThisWorkbook` in einem Projekt auf Dokumentebene für Excel und in der Klasse `ThisDocument` in einem Projekt auf Dokumentebene für Word geschrieben haben.

 Auch wenn Sie mit Word und Excel und deren Objekten arbeiten, stellt Microsoft Office die Liste der verfügbaren integrierten Dokumenteigenschaften zur Verfügung. Wenn versucht wird, auf eine nicht definierte Eigenschaft zuzugreifen, wird eine Ausnahme ausgelöst.

## <a name="see-also"></a>Weitere Informationen
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
