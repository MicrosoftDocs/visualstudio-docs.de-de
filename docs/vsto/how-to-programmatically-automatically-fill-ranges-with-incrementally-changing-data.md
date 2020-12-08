---
title: Inkrementelles ändern von Daten Bereichen automatisch ausfüllen
description: Erfahren Sie, wie Sie mithilfe der AutoFill-Methode des Bereichs Objekts einen Bereich in einem Arbeitsblatt mit Werten auffüllen können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc80b4b589eb46aefa9ef6d75384ed17bb1b7c8c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847207"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Gewusst wie: Programm gesteuertes automatisches Auffüllen von Bereichen mit inkrementellen Änderungs Daten
  Mit der- <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode des- <xref:Microsoft.Office.Interop.Excel.Range> Objekts können Sie einen Bereich in einem Arbeitsblatt mit Werten automatisch auffüllen. In den meisten Fällen <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> wird die-Methode verwendet, um inkrementelle steigende oder abnehmende Werte in einem Bereich zu speichern. Sie können das Verhalten angeben, indem Sie eine optionale Konstante aus der- <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> Enumeration bereitstellen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie verwenden, müssen Sie zwei Bereiche angeben <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Der Bereich, der die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode aufruft, die den Anfangspunkt der Füllung angibt und einen Anfangswert enthält.

- Der Bereich, den Sie ausfüllen möchten, der als Parameter an die- <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode übergeben wird. Dieser Zielbereich muss den Bereich enthalten, der den Anfangswert enthält.

    > [!NOTE]
    > Anstelle von kann ein-Steuerelement übergeben werden <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Interop.Excel.Range> . Weitere Informationen finden Sie Unterprogramm gesteuerte [Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Die erste Zelle des Bereichs, den Sie ausfüllen möchten, muss einen Anfangswert enthalten.

 Das Beispiel setzt voraus, dass Sie drei Regionen ausfüllen:

- Spalte B enthält fünf Wochentage. Geben Sie als Anfangswert **Montag** in Zelle B1 ein.

- In Spalte C sind fünf Monate enthalten. Geben Sie als Anfangswert **Januar** in Zelle C1 ein.

- Spalte D soll eine Reihe von Zahlen enthalten, die für jede Zeile um zwei erhöht werden. Geben Sie für die Anfangswerte **4** in Zelle D1 und **6** in Zelle D2 ein.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
