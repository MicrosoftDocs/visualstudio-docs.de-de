---
title: 'Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern'
description: Erfahren Sie, wie Sie das Schutz Feature in Microsoft Excel verwenden können, um zu verhindern, dass Benutzer und Code Objekte in einem Arbeitsblatt ändern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b4fe6d314763c7b0d6a8b4c1ed9e8e7198e508c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526750"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern
  Die Schutzfunktion in Microsoft Office Excel verhindert, dass Objekte in einem Arbeitsblatt durch Benutzer und Code geändert werden. Standardmäßig werden alle Zellen gesperrt, nachdem der Schutz aktiviert wurde.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In Anpassungen auf Dokumentebene können Sie Arbeitsblätter mit dem Excel-Designer schützen. Sie können ein Arbeitsblatt in einem beliebigen Projekttyp auch zur Laufzeit programmgesteuert schützen.

> [!NOTE]
> Geschützten Bereichen eines Arbeitsblatts können keine Windows Forms-Steuerelemente hinzugefügt werden.

## <a name="use-the-designer"></a>Verwenden des Designers

### <a name="to-protect-a-worksheet-in-the-designer"></a>So schützen Sie ein Arbeitsblatt im Designer

1. Klicken Sie in der Gruppe **Änderungen** der Registerkarte **überprüfen** auf **Blatt schützen**.

    Das Dialogfeld **Blatt schützen** wird angezeigt. Sie können ein Kennwort festlegen und optional bestimmte Aktionen angeben, die Benutzer in einem Arbeitsblatt ausführen dürfen, z. B. Zellen formatieren oder Zeilen einfügen.

   Sie können Benutzern auch die Bearbeitung bestimmter Bereiche in geschützten Arbeitsblättern erlauben.

### <a name="to-allow-editing-in-specific-ranges"></a>So lassen Sie die Bearbeitung bestimmter Bereiche zu

1. Klicken Sie in der Gruppe **Änderungen** der Registerkarte **überprüfen** auf **Benutzern das Bearbeiten von Bereichen erlauben**.

     Das Dialogfeld **Benutzern das Bearbeiten von Bereichen erlauben** wird angezeigt. Sie können Bereiche angeben, die mithilfe eines Kennworts entsperrt werden, und Benutzer, die Bereiche ohne Kennwort bearbeiten können.

## <a name="use-code-at-run-time"></a>Verwenden von Code zur Laufzeit
 Mit dem folgenden Code wird das Kennwort (unter Verwendung der getPasswordFromUser-Variablen, die ein vom Benutzer angegebenes Kennwort enthält) festgelegt und nur das Sortieren zugelassen.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einer Anpassung auf Dokumentebene

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> -Methode des Arbeitsblatts auf. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einen VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> -Methode des aktiven Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Entfernen des Schutzes von Arbeitsblättern](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
