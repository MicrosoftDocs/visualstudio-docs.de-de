---
title: Arbeitsmappenhostelement
description: Erfahren Sie, dass das Arbeitsmappenhostelement ein Typ ist, der den Arbeitsmappentyp aus der primären Interopassembly für Microsoft Excel erweitert.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24f32f8799d2bac5c23a0f8a2ef92857d2a6f7c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847595"
---
# <a name="workbook-host-item"></a>Arbeitsmappenhostelement
  Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Excel.Workbook> -Typ aus der primären Interopassembly für Excel erweitert. Das <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt bereit, bietet jedoch auch zusätzliche Funktionen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Standardhostelement, das die Arbeitsmappe im Projekt darstellt. In VSTO-Add-In-Projekten können Sie <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente zur Laufzeit generieren.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Grundlegendes zum Arbeitsmappenhostelement in Projekten auf Dokument Ebene
 Verwenden Sie die `ThisWorkbook` -Klasse, um auf die Arbeitsmappe im Projekt zuzugreifen. Über die `ThisWorkbook` -Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn die Arbeitsmappe geöffnet bzw. geschlossen wird. Weitere Informationen finden Sie unter [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

 Die `ThisWorkbook` -Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt in der primären Interopassembly für Excel bereitstellt, können Sie auch mit `ThisWorkbook` auf das Excel-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

 Doppelklicken Sie im **Projektmappen-Explorer** auf das **ThisWorkbook** -Projektelement, um den Arbeitsmappen-Designer und die Eigenschaften und Ereignisse der Arbeitsmappe im Fenster **Eigenschaften** anzuzeigen.

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Einschränkungen für das Arbeitsmappenhostelement in Projekten auf Dokument Ebene
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement (die `ThisWorkbook` -Klasse) enthalten. Sie können dem Projekt zur Entwurfszeit keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente hinzufügen, und Sie können zur Laufzeit von einer Anpassung auf Dokumentebene keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelemente erstellen.

 Wenn Sie zur Laufzeit eine neue Excel-Arbeitsmappe erstellen, hat sie den Typ <xref:Microsoft.Office.Interop.Excel.Workbook>. Da es kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms-Steuerelemente enthalten. Weitere Informationen zum Erstellen von Arbeitsmappen zur Laufzeit finden Sie unter Gewusst [wie: Programm gesteuertes Erstellen neuer Arbeits](../vsto/how-to-programmatically-create-new-workbooks.md)Mappen.

 Das <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelement dient nicht als Container für Hoststeuerelemente. Daher können Sie der Arbeitsmappe keine sichtbaren Steuerelemente hinzufügen. Sie können jedoch Komponenten wie <xref:System.Data.DataSet>hinzufügen, sodass die Komponenten von allen Arbeitsblättern gemeinsam genutzt werden können. In einem Projekt auf Dokumentebene befinden sich die für die Arbeitsmappe verfügbare Komponenten auf den Registerkarten **Komponente** , **Daten** und **Alle Windows Forms** der **Toolbox**.

> [!NOTE]
> Die Office-Entwicklungstools in Visual Studio unterstützen keine freigegebenen Arbeitsmappen.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Grundlegendes zu arbeitsmappenhostelementen in VSTO-Add-in-Projekten
 In VSTO-Add-In-Projekten können Sie für jede Arbeitsmappe, die in Excel geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Excel.Workbook> -Hostelement generieren. Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelements die `GetVstoObject`-Methode. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Weitere Informationen
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
