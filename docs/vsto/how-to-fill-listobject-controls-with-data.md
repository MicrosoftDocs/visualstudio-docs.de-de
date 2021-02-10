---
title: 'Gewusst wie: Auffüllen von ListObject-Steuerelementen mit Daten'
description: Verwenden Sie die Datenbindung, um dem Dokument schnell Daten hinzuzufügen. Sie können auch das Listen Objekt trennen, damit es die Daten anzeigt, aber nicht mehr an die Datenquelle gebunden ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cabaf58f9e13033edee320277abcc14b55b81a13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953967"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Gewusst wie: Auffüllen von ListObject-Steuerelementen mit Daten
  Sie können die Datenbindung als Möglichkeit zum schnellen Hinzufügen von Daten zu Ihrem Dokument verwenden. Nach dem Binden der Daten an ein Listenobjekt können Sie das Listenobjekt trennen, damit es die Daten anzeigt, aber nicht länger an die Datenquelle gebunden ist.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

### <a name="to-bind-data-to-a-listobject-control"></a>So binden Sie Daten an ein ListObject-Steuerelement

1. Erstellen Sie eine <xref:System.Data.DataTable> auf Klassenebene.

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2. Fügen Sie Beispielspalten und Daten im `Startup` -Ereignishandler der `Sheet1` -Klasse (in einem Projekt auf Dokumentebene) oder der `ThisAddIn` -Klasse (in einem Projekt auf Anwendungsebene) hinzu.

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> -Methode auf, und übergeben Sie die Spaltennamen in der Reihenfolge, in der sie angezeigt werden sollen. Die Reihenfolge der Spalten im Listenobjekt kann von der Reihenfolge abweichen, in der sie in der <xref:System.Data.DataTable>angezeigt werden.

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>So trennen Sie das ListObject-Steuerelement von der Datenquelle

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> -Methode von `List1`auf.

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject> namens `list1` verfügen.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Gewusst wie: Zuordnen von ListObject-Spalten zu Daten](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject-Steuerelement](../vsto/listobject-control.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
