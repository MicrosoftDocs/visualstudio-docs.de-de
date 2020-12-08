---
title: Globaler Zugriff auf Objekte in Office-Projekten
description: Erfahren Sie, wie Sie die Globals-Klasse verwenden können, um zur Laufzeit auf mehrere verschiedene Projekt Elemente von einem beliebigen Code im Projekt zuzugreifen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e2653f314edf07c4dcca6d3afc74af64c548af35
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846388"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globaler Zugriff auf Objekte in Office-Projekten
  Wenn Sie ein Office-Projekt erstellen, generiert Visual Studio im Projekt automatisch eine Klasse mit dem Namen `Globals` . Mit der `Globals` -Klasse können Sie von beliebigem Code im Projekt aus zur Laufzeit auf mehrere verschiedene Projektelemente zugreifen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Verwenden der Globals-Klasse
 `Globals` ist eine statische Klasse, in der Verweise auf bestimmte Elemente im Projekt abgelegt sind. Mit der `Globals` -Klasse können Sie von beliebigem Code im Projekt aus zur Laufzeit auf die folgenden Elemente zugreifen:

- Die - `ThisWorkbook` und `Sheet`*n* -Klassen in einer Excel-Arbeitsmappe oder einem Vorlagenprojekt. Sie können mit den `Globals.ThisWorkbook` - und `Sheet`*n* -Eigenschaften auf diese Objekte zugreifen.

- Die `ThisDocument` -Klasse in einem Word-Dokument oder einem Vorlagenprojekt. Sie können mit der `Globals.ThisDocument` -Eigenschaft auf dieses Objekt zugreifen.

- Die- `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt. Sie können mit der `Globals.ThisAddIn` -Eigenschaft auf dieses Objekt zugreifen.

- Alle Menübänder im Projekt, das Sie mit dem Menüband-Designer angepasst haben. Sie können mit der `Globals.Ribbons` -Eigenschaft auf die Menübänder zugreifen. Weitere Informationen finden Sie unter [zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md).

- Alle Outlook-Formularbereiche in einem VSTO-Add-In-Projekt für Outlook. Sie können mit der `Globals.FormRegions` -Eigenschaft auf die Formularbereiche zugreifen. Weitere Informationen finden Sie [unter Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md).

- Ein Factoryobjekt, das Ihnen ermöglicht, Menübandsteuerelemente zu erstellen und Hostelemente zur Laufzeit in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]abzielen. Sie können mit der `Globals.Factory` -Eigenschaft auf dieses Objekt zugreifen. Dieses Objekt ist eine Instanz einer Klasse, die eine der folgenden Schnittstellen implementiert:

  - [Microsoft. Office. Tools. Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft. Office. Tools. Excel. Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft. Office. Tools. Outlook. Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft. Office. Tools. Word. Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Beispielsweise können Sie Text mithilfe der `Globals.Sheet1` -Eigenschaft in ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf `Sheet1` einfügen, wenn ein Benutzer in einem Projekt auf Dokumentebene für Excel auf eine Schaltfläche im Aktionsbereich klickt.

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

 Code, der versucht, die- `Globals` Klasse vor dem Initialisieren des Dokuments oder des VSTO-Add-Ins zu verwenden, kann eine Lauf Zeit Ausnahme auslösen. So kann beispielsweise die Verwendung von `Globals` beim Deklarieren einer Variablen auf Klassenebene fehlschlagen, da die `Globals` -Klasse vor der Instanziierung des deklarierten Objekts möglicherweise noch nicht mit Verweisen auf alle Hostelemente initialisiert wurde.

> [!NOTE]
> Die `Globals` -Klasse wird zur Entwurfszeit nie initialisiert, vom Designer werden jedoch Steuerelementinstanzen erstellt. Dies bedeutet Folgendes: Wenn Sie ein Benutzer Steuerelement erstellen, das eine Eigenschaft der `Globals` Klasse innerhalb einer Benutzer Steuerelement Klasse verwendet, müssen Sie überprüfen, ob die-Eigenschaft **null** zurückgibt, bevor Sie versuchen, das zurückgegebene-Objekt zu verwenden.

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Dokument Host Element](../vsto/document-host-item.md)
- [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
