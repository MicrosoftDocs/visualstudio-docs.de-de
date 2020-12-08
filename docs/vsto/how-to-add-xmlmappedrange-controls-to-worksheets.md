---
title: 'Gewusst wie: Hinzufügen von XmlMappedRange-Steuerelementen zu Arbeitsblättern'
description: Wenn Sie ein XML-Element einer Zelle in Microsoft Office Excel zuordnen, fügt Visual Studio dem Arbeitsblatt automatisch ein XmlMappedRange-Steuerelement hinzu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7e807a5673f27da6a852fd2c83347d1348f1f6fd
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844412"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Gewusst wie: Hinzufügen von XmlMappedRange-Steuerelementen zu Arbeitsblättern
  Wenn Sie ein XML-Element einer Zelle in Microsoft Office Excel zuordnen, fügt Visual Studio dem Arbeitsblatt automatisch ein-Steuerelement hinzu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Das- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement ist in der **Toolbox** oder im **Datenquellen** Fenster nicht verfügbar. Darüber hinaus können Steuer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Elemente nicht Programm gesteuert erstellt werden.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>So fügen Sie ein XmlMappedRange-Steuerelement zu einem Arbeitsblatt hinzu

1. Öffnen Sie die Excel-Arbeitsmappe im Visual Studio-Designer.

2. Öffnen Sie das Arbeitsblatt, dem Sie das Steuerelement hinzufügen möchten.

3. Klicken Sie auf der Registerkarte **Entwickler** auf **Quelle**.

    > [!NOTE]
    > Wenn die Registerkarte " **Entwickler** " im Menüband nicht angezeigt wird, müssen Sie Sie aktivieren. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Der Aufgabenbereich " **XML-Quelle** " wird angezeigt.

4. Klicken Sie im Aufgabenbereich der **XML-Quelle** auf **XML**-Zuordnungen.

5. Klicken Sie im Dialogfeld **XML** -Zuordnungen auf **Hinzufügen**.

     Das Dialogfeld **XML-Quelle** wird angezeigt.

6. Wählen Sie im Dialogfeld **XML-Quelle** ein XML-Schema aus, und klicken Sie auf **Öffnen**.

     Das Schema wird dem Dialogfeld **XML** -Zuordnungen hinzugefügt.

7. Klicken Sie im Dialogfeld **XML** -Zuordnungen auf **OK**.

8. Ziehen Sie ein Element aus dem **XML-Quell** Aufgabenbereich in eine Zelle im Arbeitsblatt.

     Eine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> wird erstellt und dem Projekt hinzugefügt.

    > [!NOTE]
    > Wenn Sie ein übergeordnetes Element aus dem **XML-Quell** Aufgabenbereich ziehen, wird ein- <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement erstellt.

## <a name="see-also"></a>Siehe auch
- [XmlMappedRange-Steuerelement](../vsto/xmlmappedrange-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
