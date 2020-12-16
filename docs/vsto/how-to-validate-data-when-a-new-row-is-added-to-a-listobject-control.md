---
title: Daten überprüfen, wenn das ListObject-Steuerelement eine neue Zeile hinzufügt
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Daten zu validieren, wenn einem ListObject-Steuerelement eine neue Zeile hinzugefügt wird.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e60f19da0d36c5a57f0151318d6d76b43a80de37
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528524"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Gewusst wie: Validieren von Daten, wenn einem ListObject-Steuerelement eine neue Zeile hinzugefügt wird
  Benutzer können einem <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das an Daten gebunden ist, neue Zeilen hinzufügen. Sie können die Daten des Benutzers überprüfen, bevor Sie Änderungen in einem Commit an die Datenquelle übertragen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Datenüberprüfung
 Sobald einem <xref:Microsoft.Office.Tools.Excel.ListObject> , das an Daten gebunden ist, eine Zeile hinzugefügt wird, wird das <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> -Ereignis ausgelöst. Sie können dieses Ereignis behandeln, um Ihre Datenüberprüfung durchzuführen. Wenn die Anwendung beispielsweise erfordert, dass der Datenquelle nur Mitarbeiter zwischen 18 und 65 hinzugefügt werden können, müssen Sie überprüfen, ob das eingegebene Alter innerhalb dieses Bereichs liegt, bevor die Zeile hinzugefügt wird.

> [!NOTE]
> Zusätzlich zum Client sollte die Benutzereingabe auch immer auf dem Server überprüft werden. Weitere Informationen finden Sie unter [sichere Client Anwendungen](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>So überprüfen Sie Daten, wenn dem datengebundenen ListObject-Steuerelement eine neue Zeile hinzugefügt wird

1. Erstellen Sie Variablen für die ID und <xref:System.Data.DataTable> auf Klassenebene.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Erstellen Sie ein neues, <xref:System.Data.DataTable> und fügen Sie dem- `Startup` Ereignishandler der- `Sheet1` Klasse (in einem Projekt auf Dokument Ebene) oder der- `ThisAddIn` Klasse (in einem VSTO-Add-in-Projekt) Beispiel Spalten und-Daten hinzu.

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Fügen Sie dem `list1_BeforeAddDataBoundRow` -Ereignishandler Code hinzu, um zu überprüfen, ob das eingegebene Alter innerhalb des zulässigen Bereichs liegt.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Element namens `list1` verfügen.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject-Steuerelement](../vsto/listobject-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Gewusst wie: Zuordnen von ListObject-Spalten zu Daten](../vsto/how-to-map-listobject-columns-to-data.md)
