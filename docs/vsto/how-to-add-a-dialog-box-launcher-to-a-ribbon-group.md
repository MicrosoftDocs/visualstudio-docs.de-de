---
title: 'Gewusst wie: Hinzufügen eines Dialog Feld-Start Programms zu einer Menü Bandgruppe'
description: Sie können einer beliebigen Gruppe auf einem Menüband ein Dialogfeld-Start Programm hinzufügen, mit dem verwandte Dialogfelder oder Aufgabenbereiche geöffnet werden können, in denen weitere Optionen für die Gruppe vorhanden sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85b5d6f127c6f8b2b8140e778792aa1088efe05c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844932"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Gewusst wie: Hinzufügen eines Dialog Feld-Start Programms zu einer Menü Bandgruppe
  Sie können einer beliebigen Gruppe auf einem Menüband ein Dialogfeld-Start Programm hinzufügen. Ein Dialogfeld-Start Programm ist ein kleines Symbol, das in einer Gruppe angezeigt wird. Benutzer klicken auf dieses Symbol, um verwandte Dialogfelder oder Aufgabenbereiche zu öffnen, die weitere Optionen für die Gruppe bereitstellen.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>So fügen Sie einer Menü Bandgruppe ein Dialogfeld-Start Programm hinzu

1. Wählen Sie in **Projektmappen-Explorer** die Menüband-Codedatei (*VB* -oder *CS* -Datei) aus.

2. Klicken Sie im Menü **Ansicht** auf **Designer**.

3. Klicken Sie im Menüband-Designer mit der rechten Maustaste auf eine beliebige Gruppe, und klicken Sie dann auf **DialogBoxLauncher hinzufügen**.

     Fügen Sie dem- <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> Ereignis der-Gruppe Code hinzu, um ein benutzerdefiniertes oder integriertes Dialogfeld zu öffnen.

## <a name="see-also"></a>Siehe auch
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Übersicht über das Ribbon-Objektmodell](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
