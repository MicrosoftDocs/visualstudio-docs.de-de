---
title: 'Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften'
description: Erfahren Sie, wie Sie benutzerdefinierte Dokumenteigenschaften erstellen und ändern können, wenn Sie zusätzliche Informationen mit dem Dokument speichern möchten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4897008f102600bd222a21761237acc4bcb62a30
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844295"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften
  Die oben aufgeführten Microsoft Office-Anwendung bieten integrierte Eigenschaften, die mit Dokumenten gespeichert werden. Darüber hinaus können Sie benutzerdefinierte Dokumenteigenschaften erstellen und ändern, falls Sie zusätzliche Informationen mit dem Dokument speichern möchten.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Verwenden Sie die CustomDocumentProperties-Eigenschaft eines Dokuments, um mit benutzerdefinierten Eigenschaften zu arbeiten. Verwenden Sie in einem Projekt auf Dokumentebene für Microsoft Office Excel z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> -Eigenschaft der `ThisWorkbook` -Klasse. Verwenden Sie in einem VSTO-Add-In-Projekt für Excel die <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> -Eigenschaft eines <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekts. Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties> -Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty> -Objekten ist. Sie können die Eigenschaft `Item` der Auflistung verwenden, um eine bestimmte Eigenschaft nach Name oder Index in der Auflistung abzurufen.

 Das folgende Beispiel veranschaulicht, wie eine benutzerdefinierte Eigenschaft in einer Anpassung auf Dokumentebene für Excel hinzugefügt und ihr ein Wert zugewiesen wird.

## <a name="example"></a>Beispiel
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Stabile Programmierung
 Beim Versuch, auf die `Value` -Eigenschaft für nicht definierte Eigenschaften zuzugreifen, wird eine Ausnahme ausgelöst.

## <a name="see-also"></a>Siehe auch
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)
