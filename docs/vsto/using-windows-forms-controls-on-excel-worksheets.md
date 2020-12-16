---
title: Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern
description: Erfahren Sie, wie Sie Ihren Microsoft Excel-Arbeitsmappen Windows Forms-Steuerelemente auf die gleiche Weise hinzufügen können wie Steuerelemente, die Sie Windows Forms hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 015fffa51358c3a7a13d98950392d0749560c089
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526520"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern
  Sie können Microsoft Office Excel-Arbeitsmappen Windows Forms-Steuerelemente auf die gleiche Weise hinzufügen wie Steuerelemente, die Sie Windows Forms hinzufügen. Allgemeine Informationen zum Arbeiten mit Steuerelementen in Dokumenten finden Sie unter Windows Forms-Steuer [Elemente in der Übersicht über Office-Dokumente](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Überlegungen zu Steuerelementen für Excel
 Es gibt einige Überlegungen, die für Excel spezifisch sind.

### <a name="match-control-size-to-cell-size"></a>Abgleichen der Steuerelement Größe mit der Zellgröße
 Sie können ein Steuerelement so konfigurieren, dass dessen Größe automatisch bei Änderung der Größe der übergeordneten Zelle geändert wird. Weitere Informationen finden Sie unter Gewusst [wie: Ändern der Größe von Steuerelementen innerhalb von Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Komponenten hinzufügen, die von allen Arbeitsblättern gemeinsam genutzt werden
 Sie können Komponenten, die auf allen Arbeitsblättern nutzbar sein sollen (etwa ein <xref:System.Data.DataSet>), dem Arbeitsmappen-Designer hinzufügen, statt sie den Arbeitsblättern hinzuzufügen. Die Komponente wird auf der Komponentenleiste angezeigt.

### <a name="formula-for-embedding-controls"></a>Formel zum Einbetten von Steuerelementen
 Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste** angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Exemplarische Vorgehensweise: Ändern der Arbeitsblatt Formatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Options Feldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
