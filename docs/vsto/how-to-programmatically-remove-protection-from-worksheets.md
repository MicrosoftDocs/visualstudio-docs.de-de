---
title: 'Vorgehensweise: Programm gesteuertes Entfernen des Schutzes von Arbeitsblättern'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um den Schutz von einem Microsoft Excel-Arbeitsblatt Programm gesteuert zu entfernen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 85f659248528d0d7cf4357ffe2d1c2c5f88df9e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906759"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Vorgehensweise: Programm gesteuertes Entfernen des Schutzes von Arbeitsblättern
  Sie können den Schutz programmgesteuert aus einem Microsoft Office Excel-Arbeitsblatt entfernen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Im folgenden Beispiel wird die Variable `getPasswordFromUser`befindet, die ein vom Benutzer erhaltenes Kennwort enthält.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>So heben Sie den Schutz eines Arbeitsblatts bei der Anpassung auf Dokumentebene auf

1. Wenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> -Methode des Arbeitsblatts an, und übergeben Sie ggf. das Kennwort. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>So heben Sie den Schutz für ein Arbeitsblatt in einem VSTO-Add-in auf

1. Wenden Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> -Methode des aktiven Arbeitsblatts an, und übergeben Sie ggf. das Kennwort.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
