---
title: 'Gewusst wie: Programm gesteuertes Wiederherstellen der Auswahl nach Such Vorgängen'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um die Auswahl nach Such Vorgängen in einem Microsoft Word-Dokument Programm gesteuert wiederherzustellen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 493f736ce899a0d90332418ca37a5b2825dd2d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897502"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Gewusst wie: Programm gesteuertes Wiederherstellen der Auswahl nach Such Vorgängen
  Wenn Sie Text in einem Dokument suchen und ersetzen, sollten Sie nach Abschluss der Suche die ursprüngliche Auswahl des Benutzers wiederherstellen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Der Code in der Beispiel Prozedur verwendet zwei- <xref:Microsoft.Office.Interop.Word.Range> Objekte. Eine speichert die aktuelle <xref:Microsoft.Office.Interop.Word.Selection> und eine legt das gesamte Dokument fest, das als Suchbereich verwendet werden soll.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>So stellen Sie die ursprüngliche Auswahl des Benutzers nach einer Suche wieder her

1. Erstellen Sie die <xref:Microsoft.Office.Interop.Word.Range> -Objekte für das Dokument und die aktuelle Auswahl.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. Führt den Such-und Ersetzungs Vorgang aus.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. Wählen Sie den Startbereich aus, um die ursprüngliche Auswahl des Benutzers wiederherzustellen.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   Das folgende Beispiel zeigt die vollständige Methode.

## <a name="example"></a>Beispiel
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Gewusst wie: Programm gesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Gewusst wie: Programm gesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
