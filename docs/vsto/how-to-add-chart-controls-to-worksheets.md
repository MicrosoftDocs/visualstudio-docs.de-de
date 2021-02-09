---
title: 'Gewusst wie: Hinzufügen von Diagramm Steuerelementen zu Arbeitsblättern'
description: Erfahren Sie, wie Sie einem Microsoft Office Excel-Arbeitsblatt Diagramm Steuerelemente zur Entwurfszeit und zur Laufzeit in Anpassungen auf Dokument Ebene hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fd82cf9d8d5cb15215bf7ecbfa51c735ef52a0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917399"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Gewusst wie: Hinzufügen von Diagramm Steuerelementen zu Arbeitsblättern
  Sie können <xref:Microsoft.Office.Tools.Excel.Chart> einem Microsoft Office Excel-Arbeitsblatt Steuerelemente zur Entwurfszeit und zur Laufzeit in Anpassungen auf Dokument Ebene hinzufügen. Sie können auch Steuer <xref:Microsoft.Office.Tools.Excel.Chart> Elemente zur Laufzeit in VSTO-Add-Ins hinzufügen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von Diagramm Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von Diagramm Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene](#runtimedoclevel)

- [Hinzufügen von Diagramm Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelementen finden Sie unter [Diagramm Steuer](../vsto/chart-control.md)Element.

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Hinzufügen von Diagramm Steuerelementen zur Entwurfszeit
 Sie können das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement Ihrem Arbeitsblatt auf die gleiche Weise wie ein Diagramm innerhalb der Anwendung hinzufügen.

> [!NOTE]
> Das- <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelement ist nicht über die **Toolbox** oder das **Datenquellen** Fenster verfügbar.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>So fügen Sie einem Arbeitsblatt in Excel ein Chart-Hoststeuerelement hinzu

1. Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Diagramme** auf **Spalte**, klicken Sie auf eine Kategorie von Diagrammen, und klicken Sie dann auf den gewünschten Diagrammtyp.

2. Klicken Sie im Dialogfeld **Diagramm einfügen** auf **OK**.

3. Klicken Sie auf der Registerkarte **Entwurf** in der Gruppe **Daten** auf **Daten auswählen**.

4. Klicken Sie im Dialogfeld **Datenquelle auswählen** in das Feld **Diagramm** **Datenbereich** , und deaktivieren Sie die Standardauswahl.

5. Wählen Sie im **Diagramm Blatt Daten** den Zellen Bereich aus, der die Daten für das Diagramm enthält (Zellen **a5** bis **D8**).

6. Klicken Sie im Dialogfeld **Datenquelle auswählen** auf **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Hinzufügen von Diagramm Steuerelementen zur Laufzeit in einem Projekt auf Dokument Ebene
 Sie können das <xref:Microsoft.Office.Tools.Excel.Chart> -Steuerelement dynamisch zur Laufzeit hinzufügen. Dynamisch erstellte Diagramme werden nicht im Dokument wie Hoststeuerelemente dauerhaft gespeichert, wenn das Dokument geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein Chart-Steuerelement programmgesteuert hinzu

1. Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>-Ereignishandler von `Sheet1` den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement hinzuzufügen:

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Hinzufügen von Diagramm Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können ein <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO-Add-In-Projekt hinzufügen. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Dynamisch erstellte Chart-Steuerelemente werden nicht im Arbeitsblatt wie Hoststeuerelemente dauerhaft gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein Chart-Steuerelement programmgesteuert hinzu

1. Der folgende Code generiert ein Arbeitsblatt-Hostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement hinzu.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel gelten die folgenden Anforderungen:

- Die Daten für das Diagramm sind im Bereich von A5 bis D8 im Arbeitsblatt gespeichert.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Diagramm Steuerelement](../vsto/chart-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
