---
title: 'Gewusst wie: Programm gesteuertes Öffnen von Visio-Dokumenten'
description: Erfahren Sie, wie Sie Visual Studio zum programmgesteuerten Öffnen eines Visio-Dokuments mit den Open-oder OpenEx-Methoden verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cb24851562beec0b40a8e66a38db202745f4771e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903659"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Gewusst wie: Programm gesteuertes Öffnen von Visio-Dokumenten
  Es gibt zwei Methoden zum Öffnen vorhandener Microsoft Office Visio-Dokumente: Open und OpenEx. Die OpenEx-Methode ist identisch mit der Open-Methode, mit der Ausnahme, dass Sie Argumente bereitstellt, mit denen der Aufrufer angeben kann, wie das Dokument geöffnet

 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) - und [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) -Methode.

## <a name="open-a-visio-document"></a>Öffnen eines Visio-Dokuments

### <a name="to-open-a-visio-document"></a>So öffnen Sie ein Visio-Dokument

- Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Open`-Methode auf, und übergeben Sie den vollqualifizierten Pfad des Visio-Dokuments.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Öffnen eines Visio-Dokuments mit angegebenen Argumenten

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>So öffnen Sie ein Visio-Dokument schreibgeschützt und angedockt

- Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.OpenEx`-Methode auf, geben Sie den vollqualifizierten Pfad des Visio-Dokuments an, und schließen Sie die zu verwendenden Argumente ein, in diesem Fall „Gedockt“ und „Schreibgeschützt“.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

- Ein Visio-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner " *eigene* Dateien" (Windows XP und früher) oder im Ordner " *Dokumente* " (für Windows Vista) befinden.

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Gewusst wie: Programm gesteuertes schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
