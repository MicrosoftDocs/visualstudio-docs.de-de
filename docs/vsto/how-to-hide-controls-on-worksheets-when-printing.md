---
title: 'Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 336723f60a2cd90dc63db24e981dd06e0388cb9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544806"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken
  Wenn Sie ein Microsoft Office Excel-Dokument drucken, das Windows Forms Steuerelemente enthält, werden die Steuerelemente auf dem gedruckten Arbeitsblatt angezeigt. Sie können die Steuerelemente ausblenden, wenn Sie ein Arbeitsblatt drucken.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Wenn Sie Steuerelemente ausblenden, in denen Daten angezeigt werden, z <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> . b., sind die Daten im-Steuerelement auf dem gedruckten Arbeitsblatt nicht sichtbar.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>So blenden Sie Steuerelemente aus, wenn ein Arbeitsblatt gedruckt wird

1. Erstellen oder öffnen Sie ein Excel-Projekt in Visual Studio, und vergewissern Sie sich, dass **Sheet1** im Designer sichtbar ist. Weitere Informationen zum Erstellen von Projekten finden [Sie unter Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Ziehen Sie ein-Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox**auf <xref:Microsoft.Office.Tools.Excel.Controls.Button> eine Zelle in `Sheet1` .

3. Legen Sie im Fenster **Eigenschaften** die- <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> Eigenschaft auf **false**fest.

## <a name="see-also"></a>Weitere Informationen
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Gewusst wie: Ändern der Größe von Steuerelementen in Arbeitsblatt Zellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)
