---
title: Excel-Lösungen
description: Erfahren Sie, wie Sie mithilfe von Projektvorlagen Excel automatisieren, Excel-Features erweitern und die Excel-Benutzeroberfläche anpassen können.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3833ff549b2cceb3f783afc43a4f71dacc00ecb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931278"
---
# <a name="excel-solutions"></a>Excel-Lösungen
  Visual Studio stellt Projektvorlagen bereit, die Sie verwenden können, um Anpassungen auf Dokumentebene und VSTO-Add-Ins für Microsoft Office Excel zu erstellen. Mit diesen Projektmappen können Sie Excel automatisieren, Excel-Features erweitern und die Excel-Benutzeroberfläche anpassen. Weitere Informationen zu den Unterschieden zwischen Anpassungen auf Dokument Ebene und VSTO-Add-Ins finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Dieses Thema enthält die folgenden Informationen:

- [Automatisieren Sie Excel](#automating).

- [Entwickeln Sie Anpassungen auf Dokument Ebene für Excel](#doclevel).

- [Entwickeln von VSTO-Add-Ins für Excel](#applevel).

- [Passen Sie die Benutzeroberfläche von Excel an](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Automatisieren von Excel
 Das Excel-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Excel verwenden können. Beispielsweise können Sie programmgesteuert Diagramme erstellen, Arbeitsblätter formatieren und die Werte von Bereichen und Zellen festlegen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

 Wenn Sie Excel-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente* in den Projektmappen verwenden. Dabei handelt es sich um Objekte, die bestimmte häufig verwendete Objekte im Excel-Objektmodell erweitern, z. B. das <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und das <xref:Microsoft.Office.Interop.Excel.Range> -Objekt. Die erweiterten Objekte verhalten sich wie die Excel-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis- und Datenbindungsfunktionen hinzu. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Entwickeln von Anpassungen auf Dokument Ebene für Excel
 Eine Anpassung auf Dokumentebene für Microsoft Office Excel besteht aus einer Assembly, die einer spezifischen Arbeitsmappe zugeordnet ist. Die Assembly erweitert das Dokument normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Im Gegensatz zu einem VSTO-Add-In, das Excel direkt zugeordnet ist, sind Funktionen, die in einer Anpassung implementiert werden, nur dann verfügbar, wenn die zugehörige Arbeitsmappe in Word geöffnet ist.

 Um ein Anpassungs Projekt auf Dokument Ebene für Excel zu erstellen, verwenden Sie die Projektvorlagen für Excel-Arbeits mappenvorlagen oder Excel-Vorlagen im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Weitere Informationen zur Funktionsweise von Anpassungen auf Dokument Ebene finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Programmiermodell für die Anpassung von Excel
 Wenn Sie ein Projekt auf Dokumentebene für Excel erstellen, generiert Visual Studio mehrere Klassen, die die Grundlage für die Projektmappe bilden: `ThisWorkbook`, `Sheet1`, `Sheet2`und `Sheet3`. Diese Klassen stellen die Arbeitsmappe und die Arbeitsblätter dar, die der Projektmappe zugeordnet sind, und sie bieten einen Ausgangspunkt zum Schreiben von Code.

 Weitere Informationen zu diesen generierten Klassen und anderen Features, die Sie in einem Projekt auf Dokument Ebene verwenden können, finden Sie unter [Program mieren von Programmen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Entwickeln von VSTO-Add-Ins für Excel
 Ein VSTO-Add-In für Microsoft Office Excel besteht aus einer Assembly, die von Excel geladen wird. Die Assembly erweitert Excel normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Anders als bei einer Anpassung auf Dokument Ebene, die einer bestimmten Arbeitsmappe zugeordnet ist, sind Funktionen, die in einem VSTO-Add-in implementiert werden, nicht auf eine einzelne Arbeitsmappe beschränkt.

 Um ein VSTO-Add-in-Projekt für Excel zu erstellen, verwenden Sie die Projektvorlagen für Excel-Arbeits mappenvorlagen oder Excel-Vorlagen im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Allgemeine Informationen über die Funktionsweise von VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Excel-Add-in-Programmiermodell
 Wenn Sie ein Excel-VSTO-Add-In-Projekt erstellen, generiert Visual Studio eine Klasse namens `ThisAddIn`, die die Grundlage der Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben von Code, und sie macht auch das Excel-Objektmodell für das VSTO-Add-In verfügbar.

 Weitere Informationen zur `ThisAddIn` -Klasse und anderen Visual Studio-Funktionen, die Sie in einem VSTO-Add-in verwenden können, finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Anpassen der Benutzeroberfläche von Excel
 Es gibt mehrere Möglichkeiten, die Benutzeroberfläche von Excel anzupassen. Einige Optionen sind für alle Projekttypen verfügbar, andere Optionen sind jedoch nur für VSTO-Add-Ins oder Anpassungen auf Dokumentebene verfügbar.

### <a name="options-for-all-project-types"></a>Optionen für alle Projekttypen
 In der folgenden Tabelle sind die Anpassungsoptionen aufgeführt, die sowohl für Anpassungen auf Dokumentebene als auch für VSTO-Add-Ins zur Verfügung stehen.

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Anpassen des Menübands|[Übersicht über Menüband](../vsto/ribbon-overview.md)|
|Hinzufügen von Windows Forms-Steuerelementen oder erweiterten Excel-Steuerelementen zu einem Arbeitsblatt in der angepassten Arbeitsmappe (für eine Anpassung auf Dokumentebene) oder zu einer beliebigen geöffneten Arbeitsmappe (für ein VSTO-Add-In).|[Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Gewusst wie: Hinzufügen von Diagramm Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Gewusst wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Optionen für Anpassungen auf Dokument Ebene
 In der folgenden Tabelle sind Anpassungsoptionen aufgeführt, die nur für Anpassungen auf Dokumentebene zur Verfügung stehen.

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Fügen Sie der Arbeitsmappe einen Aktionsbereich hinzu.|[Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)<br /><br /> [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Fügen Sie einem Arbeitsblatt erweiterte Bereichssteuerelemente hinzu, die XML-Knoten zugeordnet sind.|[Gewusst wie: Hinzufügen von XmlMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Optionen für VSTO-Add-Ins
 In der folgenden Tabelle werden Anpassungsoptionen aufgeführt, die nur für VSTO-Add-Ins zur Verfügung stehen.

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Verwandte Themen

| Titel | Beschreibung |
| - | - |
| [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md) | Hier finden Sie eine Übersicht über die wichtigsten Typen im Excel-Objektmodell. |
| [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md) | Hier finden Sie Informationen zu erweiterten Objekten (der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), die in Excel-Projektmappen verwendet werden können. |
| [Globalisierung und Lokalisierung von Excel-Lösungen](../vsto/globalization-and-localization-of-excel-solutions.md) | Enthält besondere Überlegungen zu Excel-Projektmappen, die auf Computern ausgeführt werden, die über nicht englische Einstellungen für Windows verfügen. |
| [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md) | Hier wird beschrieben, wie Sie Excel-Arbeitsblättern Windows Forms-Steuerelemente hinzufügen können. |
| [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen. |
| [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Veranschaulicht die Erstellung eines grundlegenden VSTO-Add-Ins für Excel. |
| [Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit im VSTO-Add-in-Projekt](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Veranschaulicht, wie Sie einem Arbeitsblatt zur Laufzeit mithilfe eines VSTO-Add-Ins eine Windows Forms-Schaltfläche, ein <xref:Microsoft.Office.Tools.Excel.NamedRange>und ein <xref:Microsoft.Office.Tools.Excel.ListObject> hinzufügen können. |
| [Grundlegendes zur gemeinsamen Erstellung und zu Add-ins](./understanding-coauthoring-and-addins.md) | Beschreibt Anpassungen, die Sie möglicherweise an Ihren Lösungen vornehmen müssen, um die Erstellung von coerstellungen zu ermöglichen |
| [Excel 2010 bei der Office-Entwicklung](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Enthält Links zu Artikeln und Referenzdokumentation zur Entwicklung von Excel-Projektmappen. Diese sind nicht spezifisch für die Office-Entwicklung mit Visual Studio. |
