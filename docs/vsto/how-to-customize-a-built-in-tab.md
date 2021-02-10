---
title: 'Gewusst wie: Anpassen einer integrierten Registerkarte'
description: Erfahren Sie, wie Sie einer integrierten Registerkarte Gruppen und Steuerelemente hinzufügen können. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office Anwendung befindet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94cf4d256cafa03ee4604138f7233ff9fd3cf6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953993"
---
# <a name="how-to-customize-a-built-in-tab"></a>Gewusst wie: Anpassen einer integrierten Registerkarte
  Sie können einer integrierten Registerkarte Gruppen und Steuerelemente hinzufügen. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office Anwendung befindet. Beispielsweise ist die Registerkarte " **Daten** " eine integrierte Registerkarte in Excel. Wenn Sie eine benutzerdefinierte Gruppe erstellen, wird diese auf der Registerkarte an letzter Stelle angezeigt. Sie können die Gruppe aber an eine beliebige Position auf der Registerkarte verschieben.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Sie können einer integrierten Registerkarte Gruppen hinzufügen, die integrierten Gruppen jedoch nicht von einer integrierten Registerkarte entfernen.

### <a name="to-add-groups-to-a-built-in-tab"></a>So fügen Sie einer integrierten Registerkarte Gruppen hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Menüband-Codedatei, und klicken Sie dann auf **Designer anzeigen**

    > [!NOTE]
    > Wenn die Menüband-Codedatei nicht in **Projektmappen-Explorer** angezeigt wird, müssen Sie dem Projekt ein Menü **Band Element** hinzufügen. Weitere Informationen finden [Sie unter Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Klicken Sie mit der rechten Maustaste auf eine beliebige Registerkarte im Menüband-Designer und dann auf **Eigenschaften**.

3. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **ControlID** , und legen Sie dann die Eigenschaft **ControlIdType** auf **Office** fest.

4. Legen Sie die **OfficeId-** Eigenschaft auf die Steuerelement- *ID* der integrierten Registerkarte fest, die Sie anpassen möchten.

     Die Steuerelement-ID ist der Name, mit dem Registerkarten, Gruppen und Steuerelemente eindeutig identifiziert werden, die in Microsoft Office-Anwendungen integriert sind.

     Eine Liste der Steuerelement-IDs finden Sie in den [Hilfedateien von Office 2010: überflüssige Office-Steuer](https://www.microsoft.com/download/details.aspx?id=6627)Element Bezeichner.

5. Ziehen Sie Gruppen auf der Registerkarte Steuer **Elemente für Office** -Menü Bänder der **Toolbox** auf die Registerkarte.

    > [!NOTE]
    > Integrierte Gruppen werden im Designer nicht angezeigt. Daher können Sie nur bestimmen, ob Sie mit einer integrierten Registerkarte arbeiten, indem Sie die **ControlID** -Eigenschaft der Registerkarte überprüfen.

### <a name="to-position-groups-on-a-built-in-tab"></a>So ordnen Sie Gruppen auf einer integrierten Registerkarte an

1. Wählen Sie im Menüband-Designer eine benutzerdefinierte Gruppe aus.

2. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position** .

3. Legen Sie die **PositionType** -Eigenschaft auf den entsprechenden Wert fest:

    - **BeforeOfficeId** positioniert die Gruppe vor einer angegebenen integrierten Gruppe.

    - **AfterOfficeId** positioniert die Gruppe nach einer angegebenen integrierten Gruppe.

4. Legen Sie die **OfficeId-** Eigenschaft auf die Steuerelement-ID einer integrierten Gruppe fest.

     Eine Liste der Steuerelement-IDs finden Sie in den [Hilfedateien von Office 2010: überflüssige Office-Steuer](https://www.microsoft.com/download/details.aspx?id=6627)Element Bezeichner.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern](../vsto/how-to-show-add-in-user-interface-errors.md)
