---
title: 'Gewusst wie: Programm gesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen'
description: Erfahren Sie, wie Sie die Add-Methode des Rows-Objekts verwenden können, um der Tabelle Zeilen hinzuzufügen. Sie können auch die Add-Methode des Columns-Objekts verwenden, um Spalten hinzuzufügen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10154033c23cccc134752afb7f8b1e9c67099671
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846362"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Gewusst wie: Programm gesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen
  In einer Microsoft Office Word-Tabelle werden die Zellen in Zeilen und Spalten angeordnet. Sie können die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Rows>-Objekts verwenden, um der Tabelle Zeilen hinzuzufügen, und die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Columns>-Objekts, um Spalten hinzuzufügen.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Beispiele für die Anpassung auf Dokument Ebene
 Die folgenden Codebeispiele können in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie diese Beispiele verwenden möchten, führen Sie den Code von der `ThisDocument`-Klasse im Projekt aus. In diesen Beispielen wird davon ausgegangen, dass das mit der Anpassung verknüpfte Dokument bereits über mindestens eine Tabelle verfügt.

> [!IMPORTANT]
> Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:
>
> - Word 2013-Dokument
> - Word 2013-Vorlage
> - Word 2010-Dokument
> - Word 2010-Vorlage
>
>   Wenn Sie diese Aufgabe in einem beliebigen anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft. Office. Interop. Word** -Assembly hinzufügen. Anschließend müssen Sie Klassen aus dieser Assembly verwenden, um den Tabellenzeilen und Spalten hinzuzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer](how-to-target-office-applications-through-primary-interop-assemblies.md) Interopassemblys und Referenz für primäre Interopassemblys für [Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>So fügen Sie einer Tabelle eine Zeile hinzu

1. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode, um der Tabelle eine Zeile hinzuzufügen.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>So fügen Sie einer Tabelle eine Spalte hinzu

1. Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>-Methode, um alle Spalten mit der gleichen Breite zu formatieren.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>VSTO-Add-in-Beispiele
 Die folgenden Codebeispiele können in einem VSTO-Add-In verwendet werden. Wenn Sie diese Beispiele verwenden möchten, führen Sie sie von der `ThisAddIn`-Klasse im Projekt aus. In diesen Beispielen wird davon ausgegangen, dass das aktive Dokument bereits über mindestens eine Tabelle verfügt.

> [!IMPORTANT]
> Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe der VSTO-Add-In-Vorlagen für Word erstellen.
>
> Wenn Sie diese Aufgabe in einem beliebigen anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft. Office. Interop. Word** -Assembly hinzufügen. Anschließend müssen Sie Klassen aus dieser Assembly verwenden, um den Tabellenzeilen und Spalten hinzuzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer](how-to-target-office-applications-through-primary-interop-assemblies.md) Interopassemblys und Referenz für primäre Interopassemblys für [Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>So fügen Sie einer Tabelle eine Zeile hinzu

1. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode, um der Tabelle eine Zeile hinzuzufügen.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>So fügen Sie einer Tabelle eine Spalte hinzu

1. Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>-Methode, um alle Spalten mit der gleichen Breite zu formatieren.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Programm gesteuertes Erstellen von Word-Tabellen](how-to-programmatically-create-word-tables.md)
- [Gewusst wie: Programm gesteuertes Hinzufügen von Text und Formatierung zu Zellen in Word-Tabellen](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Gewusst wie: Programm gesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](how-to-programmatically-populate-word-tables-with-document-properties.md)
