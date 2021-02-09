---
title: 'Gewusst wie: Programm gesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen'
description: Erfahren Sie, wie Sie die Position von Arbeitsblättern in Bezug auf andere Arbeitsblätter in einer Microsoft Excel-Arbeitsmappe Programm gesteuert ändern können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 427f3f47e141d9c3ae17bab4b253389c68d4dc1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888783"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Gewusst wie: Programm gesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen
  Sie können die Position von Arbeitsblättern relativ zu anderen Arbeitsblättern in einer Arbeitsmappe programmgesteuert ändern. Wenn Sie keine Position für das zu verschiebende Blatt angeben, erstellt Excel eine neue Arbeitsmappe, in der das Blatt enthalten ist.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>So verschieben Sie ein Arbeitsblatt in einer Anpassung auf Dokumentebene

1. Weisen Sie die Gesamtzahl von Blättern in der Arbeitsmappe einer Variablen zu, und verschieben Sie dann das erste Arbeitsblatt so, dass es zum letzten Blatt wird.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>So verschieben Sie ein Arbeitsblatt in einem VSTO-Add-in

1. Weisen Sie die Gesamtzahl von Blättern in der Arbeitsmappe einer Variablen zu, und verschieben Sie dann das erste Arbeitsblatt so, dass es zum letzten Blatt wird.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
