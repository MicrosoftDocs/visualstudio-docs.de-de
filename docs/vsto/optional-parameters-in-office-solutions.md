---
title: Optionale Parameter in Office-Projektmappen
description: Erfahren Sie, wie Sie einen Wert für optionale Parameter nicht übergeben müssen, da die Standardwerte automatisch für jeden fehlenden Parameter verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d6824d53d552a27a68a49d63497156147283fd29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847699"
---
# <a name="optional-parameters-in-office-solutions"></a>Optionale Parameter in Office-Projektmappen
  Viele der Methoden in den Objektmodellen von Microsoft Office-Anwendungen akzeptieren optionale Parameter. Wenn Sie mithilfe von Visual Basic eine Office-Lösung in Visual Studio entwickeln, muss kein Wert für optionale Parameter übergeben werden, da die Standardwerte automatisch für jeden fehlenden Parameter verwendet werden. In den meisten Fällen können optionale Parameter in Visual C#-Projekten auch weggelassen werden. Sie können jedoch keine optionalen **ref** -Parameter der- `ThisDocument` Klasse in Word-Projekten auf Dokument Ebene weglassen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Weitere Informationen zum Arbeiten mit optionalen Parametern in Visual c#-und Visual Basic Projekten finden Sie unter [benannte und optionale Argumente &#40;C&#35;-Programmier Leit Faden&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) und [optionale Parameter &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> In früheren Versionen von Visual Studio müssen Sie einen Wert für jeden optionalen Parameter in Visual C#-Projekten übergeben. Zur Vereinfachung schließen diese Projekte eine globale Variable mit dem Namen `missing` ein, die Sie an einen optionalen Parameter übergeben können, wenn Sie den Standardwert des Parameters verwenden möchten. Visual c#-Projekte für Office in Visual Studio enthalten weiterhin die- `missing` Variable, aber Sie müssen Sie in der Regel nicht verwenden, wenn Sie Office-Projektmappen in entwickeln [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , außer wenn Sie Methoden mit optionalen **ref** -Parametern in der- `ThisDocument` Klasse in Projekten auf Dokument Ebene für Word aufruft.

## <a name="example-in-excel"></a>Beispiel in Excel
 Die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>-Methode verfügt über viele optionale Parameter. Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen (siehe folgendes Codebeispiel). Dieses Beispiel erfordert ein Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Beispiel in Word
 Die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>-Methode verfügt über viele optionale Parameter. Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen (siehe folgendes Codebeispiel).

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Optionale Parameter von Methoden in der ThisDocument-Klasse in Visual c#-Projekten auf Dokument Ebene für Word verwenden
 Das Word-Objektmodell enthält viele Methoden mit optionalen **ref** -Parametern, die- <xref:System.Object> Werte akzeptieren.  `ThisDocument` In Visual c#-Projekten auf Dokument Ebene für Word können Sie jedoch keine optionalen ref-Parameter der Methoden der generierten-Klasse weglassen. Visual c# ermöglicht es Ihnen, optionale **ref** -Parameter nur für Methoden der Schnittstellen, nicht für Klassen, auszulassen. Beispielsweise wird das folgende Codebeispiel nicht kompiliert, da Sie keine optionalen **ref** -Parameter der-Methode der-Klasse weglassen können <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> `ThisDocument` .

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 Wenn Sie Methoden der `ThisDocument`-Klasse aufrufen, befolgen Sie diese Richtlinien:

- Übergeben Sie die Variable an den-Parameter, um den Standardwert eines optionalen **ref** -Parameters zu akzeptieren `missing` . Die `missing`-Variable wird automatisch in Visual C# Office-Projekten definiert und dem <xref:System.Type.Missing>-Wert im generierten Projektcode zugewiesen.

- Um einen eigenen Wert für einen optionalen **ref** -Parameter anzugeben, deklarieren Sie ein Objekt, das dem Wert zugewiesen ist, den Sie angeben möchten, und übergeben Sie dann das Objekt an den-Parameter.

  Im folgenden Codebeispiel wird veranschaulicht, wie Sie die-Methode aufrufen, <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> indem Sie einen Wert für den *IgnoreUppercase* -Parameter angeben und den Standardwert für die anderen Parameter akzeptieren.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  Wenn Sie Code schreiben möchten, der optionale **ref** -Parameter einer Methode in der-Klasse auslässt `ThisDocument` , können Sie die gleiche Methode auch für das <xref:Microsoft.Office.Interop.Word.Document> von der-Eigenschaft zurückgegebene Objekt aufzurufen <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> und die Parameter dieser Methode weglassen. Dies ist möglich, da <xref:Microsoft.Office.Interop.Word.Document> eine Schnittstelle und keine Klasse ist.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  Weitere Informationen zu Wert-und Verweistyp Parametern finden Sie unter [übergeben von Argumenten als Wert und als Verweis &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (für Visual Basic) und [übergeben von Parametern &#40;C&#35; Programmier Handbuch&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
