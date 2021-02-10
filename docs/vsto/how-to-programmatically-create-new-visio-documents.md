---
title: 'Gewusst wie: Programm gesteuertes Erstellen neuer Visio-Dokumente'
description: Erfahren Sie, wie Sie Programm gesteuert ein neues Microsoft Visio-Zeichnungs Dokument erstellen und es der Documents-Sammlung offener Visio-Dokumente hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5aeddeecf7fb76000817f2c57b90e30465fa4ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964029"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Gewusst wie: Programm gesteuertes Erstellen neuer Visio-Dokumente
  Wenn Sie ein neues Microsoft Office Visio-Zeichnungsdokument erstellen, fügen Sie dieses Dokument der `Microsoft.Office.Interop.Visio.Documents`-Auflistung geöffneter Visio-Dokumente hinzu. Daher wird ein neues Visio-Zeichnungsdokument mithilfe der `Microsoft.Office.Interop.Visio.Documents.Add`-Methode erstellt. Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) -Methode.

## <a name="create-new-blank-documents"></a>Erstellen neuer leerer Dokumente

### <a name="to-create-a-new-document"></a>So erstellen Sie ein neues Dokument

- Verwenden Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode, um ein neues leeres Dokument zu erstellen, das nicht auf einer Vorlage basiert.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Erstellen von aus vorhandenen Dokumenten kopierten Dokumenten
 Mit der `Microsoft.Office.Interop.Visio.Documents.Add`-Methode können Sie ein neues Dokument erstellen, das eine Kopie eines vorhandenen Visio-Dokuments ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad des Diagramms angeben.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>So erstellen Sie ein neues Dokument, das aus einem vorhandenen Dokument kopiert wird

- Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad zum Visio-Diagramm an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Erstellen von aus vorhandenen Schablonen kopierten Schablonen
 Mit der [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) -Methode können Sie eine neue Schablone erstellen, die eine Kopie einer vorhandenen Visio-Schablone ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Schablone angeben.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>So erstellen Sie eine neue Schablone, die aus einer vorhandenen Schablone kopiert wird

- Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad der Schablone an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Erstellen von Dokumenten auf der Grundlage vorhandener Vorlagen
 Die- `Microsoft.Office.Interop.Visio.Documents.Add` Methode kann ein neues Dokument (eine *VSD* -Datei) erstellen, das auf einer vorhandenen Visio-Vorlage (einer *. VST* -Datei) basiert. Diese Methode kopiert die Schablonen, Formate und Einstellungen, die Bestandteile des Vorlagenarbeitsbereichs sind. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>So erstellen Sie ein neues Dokument, das auf einer vorhandenen Vorlage basiert

- Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad der Vorlage an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

- Ein Visio-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner " *eigene* Dateien" (Windows XP und früher) oder im Ordner " *Dokumente* " (für Windows Vista) befinden.

- Ein Visio-Dokument namens `myStencil.vss` muss sich in einem Verzeichnis namens `Test` im Ordner " *eigene* Dateien" (Windows XP und früher) oder im Ordner " *Dokumente* " (für Windows Vista) befinden.

- Ein Visio-Dokument namens `myTemplate.vst` muss sich in einem Verzeichnis namens `Test` im Ordner " *eigene* Dateien" (Windows XP und früher) oder im Ordner " *Dokumente* " (für Windows Vista) befinden.

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Gewusst wie: Programm gesteuertes schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
