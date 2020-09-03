---
title: 'Gewusst wie: Programm gesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblatt Zelle'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ed93451942ccb0376c78ebb0e99b269a658131de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545924"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Gewusst wie: Programm gesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblatt Zelle
  In diesem Beispiel wird veranschaulicht, wie Text in einer Zelle Programm gesteuert angezeigt wird. Verwenden Sie zum Anzeigen von Text in einer Zelle entweder ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein System eigenes Excel-Bereichs Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden eines NamedRange-Steuer Elements
 Dieses Beispiel verwendet ein-Steuerelement mit dem <xref:Microsoft.Office.Tools.Excel.NamedRange> Namen `message` . Das-Steuerelement muss zu einer Anpassung auf Dokument Ebene zur Entwurfszeit hinzugefügt werden. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der- `ThisWorkbook` Klasse.

### <a name="to-display-text-in-a-namedrange-control"></a>So zeigen Sie Text in einem Name Drange-Steuerelement an

1. Legen Sie den Wert des- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuer Elements auf **Hallo Welt**fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Verwenden eines nativen Excel-Bereichs
 Mit dem folgenden Code wird ein neuer Bereich Programm gesteuert erstellt und dann ein Wert zugewiesen.

### <a name="to-display-text-in-an-excel-range"></a>So zeigen Sie Text in einem Excel-Bereich an

1. Rufen Sie den Bereich in der Zelle **a1** ab `Sheet1` , und legen Sie den Wert auf **Hallo Welt**fest.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Problembehandlung für Office-Lösungen](../vsto/troubleshooting-office-solutions.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
