---
title: Programm gesteuertes kopieren und Einfügen von Shapes in ein Visio-Dokument
description: Erfahren Sie, wie Sie Formen Programm gesteuert auf eine Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4643d1527d078639e2f2f09add42fff96e345091
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523202"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Gewusst wie: Programm gesteuertes kopieren und Einfügen von Shapes in ein Visio-Dokument
  Sie können programmgesteuert Shapes auf einer Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen. Sie können die Shapes wahlweise an der Standardposition (in der Mitte des aktiven Fensters) oder an der gleichen Koordinatenpositionen wie auf der ursprünglichen Seite einfügen.

## <a name="copy-and-paste-shapes"></a>Kopieren und Einfügen von Formen
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)und [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>So kopieren Sie Shapes in die Mitte einer anderen Seite

- Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und in der Mitte der zweiten Seite einfügen.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopieren und Einfügen von Formen mit denselben Positionen
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)und [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Wenn Sie das Format der eingefügten Informationen steuern und (optional) einen Link zu einer Quelldatei (z. b. ein Microsoft Office Word-Dokument) herstellen müssen, verwenden Sie die PasteSpecial-Methode.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>So kopieren Sie Shapes und ihre Positionen auf eine andere Seite

- Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und auf der zweiten Seite an ihren ursprünglichen Koordinatenpositionen einfügen.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)
- [Gewusst wie: Programm gesteuertes Hinzufügen von Shapes zu einem Visio-Dokument](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
