---
title: Späte Bindung in Office-Projektmappen
description: Erfahren Sie, wie einige Typen in Objekt Modellen innerhalb Microsoft Office Anwendungen Funktionen bereitstellen, die über Funktionen mit späterer Bindung verfügbar sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 455816b2e23a25ad5ef83c726b2a78e4245ed99a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927651"
---
# <a name="late-binding-in-office-solutions"></a>Späte Bindung in Office-Projektmappen
  Einige Typen in den Objekt Modellen von Office-Anwendungen stellen Funktionen bereit, die über Funktionen mit späterer Bindung verfügbar sind. Beispielsweise können einige Methoden und Eigenschaften abhängig vom Kontext der Office-Anwendung verschiedene Objekttypen zurückgeben, und einige Typen können unterschiedliche Methoden oder Eigenschaften in verschiedenen Kontexten verfügbar machen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic Projekte, bei denen " **Option Strict** " deaktiviert ist und Visual c#-Projekte, die auf oder ausgerichtet sind, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] direkt mit Typen arbeiten können, die diese Funktionen mit späterer Bindung verwenden.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Implizites und explizites umwandeln von Objekt Rückgabe Werten
 Viele Methoden und Eigenschaften in den Microsoft Office primären Interop-Assemblys (PIAs) geben <xref:System.Object> Werte zurück, da Sie mehrere verschiedene Objekttypen zurückgeben können. Beispielsweise gibt die- <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> Eigenschaft einen zurück, <xref:System.Object> da der Rückgabewert ein-oder-Objekt sein kann <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> , je nachdem, was das aktive Blatt ist.

 Wenn eine Methode oder Eigenschaft einen zurückgibt <xref:System.Object> , müssen Sie das Objekt explizit (in Visual Basic) in den richtigen Typ in Visual Basic Projekten konvertieren, bei denen " **Option Strict" aktiviert** ist. Sie müssen <xref:System.Object> Rückgabewerte nicht explizit in Visual Basic Projekte umwandeln, bei denen " **Option Strict** " deaktiviert ist.

 In den meisten Fällen listet die Referenz Dokumentation die möglichen Typen des Rückgabewerts für einen Member auf, der einen zurückgibt <xref:System.Object> . Beim Konvertieren oder Umwandeln des-Objekts wird IntelliSense für das-Objekt im Code-Editor aktiviert.

 Informationen zur Konvertierung in Visual Basic finden Sie unter [implizite und explizite Konvertierungen &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und [CType-Funktion &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;.

### <a name="examples"></a>Beispiele
 Im folgenden Codebeispiel wird veranschaulicht, wie ein-Objekt in einen bestimmten Typ in einem Visual Basic Projekt umgewandelt wird, in dem **Option Strict aktiviert** ist. In diesem Projekttyp müssen Sie die- <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft explizit in einen umwandeln <xref:Microsoft.Office.Interop.Excel.Range> . Dieses Beispiel erfordert ein Excel-Projekt auf Dokument Ebene mit einer Arbeitsblatt Klasse mit dem Namen `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt implizit in einen bestimmten Typ in einem Visual Basic Projekt umgewandelt wird, wobei **Option Strict** deaktiviert ist, oder in einem Visual c#-Projekt, das auf abzielt [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In diesen Projekttypen wird die- <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft implizit in einen umgewandelt <xref:Microsoft.Office.Interop.Excel.Range> . Dieses Beispiel erfordert ein Excel-Projekt auf Dokument Ebene mit einer Arbeitsblatt Klasse mit dem Namen `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Zugreifen auf Member, die nur über die späte Bindung verfügbar sind
 Einige Eigenschaften und Methoden in den Office-PIAs sind nur über die späte Bindung verfügbar. In Visual Basic Projekten, in denen **Option Strict** deaktiviert ist, oder in Visual c#-Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder ausgerichtet [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] sind, können Sie die späten Bindungsfunktionen in diesen Sprachen verwenden, um auf spät gebundene Member zuzugreifen. In Visual Basic Projekten, in denen **Option Strict aktiviert** ist, müssen Sie die Reflektion verwenden, um auf diese Member zuzugreifen.

### <a name="examples"></a>Beispiele
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie in einem Visual Basic Projekt auf spät gebundene Member zugreifen können, wenn **Option Strict** deaktiviert ist, oder in einem Visual c#-Projekt, das auf abzielt [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In diesem Beispiel wird auf die Eigenschaft für den spät gebundenen **Namen** des Dialog Felds zum **Öffnen von Dateien** in Word zugegriffen. Um dieses Beispiel zu verwenden, führen Sie es von der- `ThisDocument` Klasse oder- `ThisAddIn` Klasse in einem Word-Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Im folgenden Codebeispiel wird veranschaulicht, wie Reflektion verwendet wird, um die gleiche Aufgabe in einem Visual Basic-Projekt auszuführen, bei dem " **Option Strict" aktiviert** ist.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Weitere Informationen
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Verwenden Sie den Typ Dynamic &#40;C&#35; Programming Guide&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
