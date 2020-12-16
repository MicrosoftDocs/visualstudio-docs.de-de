---
title: Multifunktionsleisten-Designer
description: Erfahren Sie, wie Sie mit dem Menüband-Designer dem Menüband einer Microsoft Office Anwendung benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b72270da75d27ed2837540369f74e9c5e87b417b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528005"
---
# <a name="ribbon-designer"></a>Multifunktionsleisten-Designer
  Der Menüband-Designer ist ein visueller Entwurfzeichnungsbereich. Verwenden Sie den Menüband-Designer, um dem Menüband einer Microsoft Office Anwendung benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzuzufügen.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Um den Menüband-Designer zu öffnen, fügen Sie dem Projekt ein Element mit dem **Menüband (visueller Designer)** hinzu. Anschließend können die Entwurftools für die folgenden Aufgaben verwendet werden:

- [Entwerfen des Menübandlayouts](#DesigningRibbonLayout)

- [Behandeln von Ereignissen und Festlegen der Steuerelementeigenschaften](#HandleEventsSetProperties)

- [Hinzufügen von Steuerelementen zur Backstage-Ansicht](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Einige Aufgaben können mit dem Menüband-Designer nicht ausgeführt werden. Weitere Informationen zu diesen Aufgaben und deren erreichen finden Sie unter Übersicht über das [Menüband](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Hinzufügen eines Elements "Menüband (visueller Designer)" zu einem Projekt
 Um den Menüband-Designer zu verwenden, fügen Sie dem Projekt ein neues **Menüband-Element (visuelles Designer)** hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Wenn Sie ein neues Element für das **Menüband (visueller Designer)** hinzufügen, fügt Visual Studio dem Projekt automatisch die folgenden Dateien hinzu:

- Eine Menüband-Codedatei. Diese Datei enthält den Namen, den Sie für das Element **Menüband (visueller Designer)** im Dialogfeld **Neues Element hinzufügen** angeben. Fügen Sie dieser Datei zum Behandeln der Menübandereignisse Code hinzu.

- Eine Codedatei des Menüband-Designers. Diese Datei beinhaltet vom Menüband-Designer generierten Code und sollte nicht direkt bearbeitet werden.

- Eine Ressourcendatei. Diese Datei enthält die Eigenschaftswerte der einzelnen Steuerelemente auf dem Menüband.

  Wenn Sie bereits über ein Element im **Menüband (visueller Designer)** aus einem anderen Projekt verfügen, können Sie es in Ihrem aktuellen Projekt wieder verwenden, indem Sie das Dialogfeld **Vorhandenes Element hinzufügen** verwenden.

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Entwerfen eines Menübands
 Zum Öffnen des Menüband-Designers stehen drei Möglichkeiten zur Verfügung:

- Doppelklicken Sie in **Projektmappen-Explorer** auf die Menüband-Codedatei.

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Menüband-Codedatei, und klicken Sie dann auf **Designer anzeigen**.

- Wählen Sie in **Projektmappen-Explorer** die Menüband-Codedatei aus, und klicken Sie dann im Menü **Ansicht** auf **Designer** .

  Der Menüband-Designer beinhaltet eine Standardregisterkarte und -gruppe. Standardregisterkarte und -gruppe können aus dem Menüband-Designer entfernt werden. Klicken Sie mit der rechten Maustaste auf **group1**, und klicken Sie dann auf **Löschen**, um die Standardgruppe zu entfernen. Klicken Sie zum Entfernen der Standard Registerkarte mit der rechten Maustaste auf einen leeren Bereich der Entwurfs Oberfläche, und klicken Sie dann auf **Registerkarte des Menübands entfernen**.

  Dem Menüband-Designer können auch benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzugefügt werden. Sie finden diese Steuerelemente in der **Toolbox** in der Gruppe " **Office-Menüband** -Steuerelemente". Es gibt drei Möglichkeiten zum Hinzufügen von Steuerelementen aus der Gruppe **Office-Menüband** -Steuerelemente zum Menüband-Designer

- Ein Steuerelement in einen geeigneten Bereich im Menüband-Designer ziehen.

- Auf ein Steuerelement und anschließend in einen geeigneten Bereich im Menüband-Designer klicken.

- Wählen Sie einen geeigneten Bereich im Designer aus, und doppelklicken Sie dann auf ein Steuerelement in der **Toolbox**.

### <a name="ribbon-design-workflow"></a>Workflow Design-Workflow
 Führen Sie folgende grundlegende Schritte zum Entwerfen des Menübandlayouts aus:

1. [Fügen Sie dem Menüband eine benutzerdefinierte Registerkarte hinzu](#AddTabToRibbon).

2. [Fügen Sie der Registerkarte Gruppen hinzu](#AddGroupsToTab).

3. [Fügen Sie den Gruppen Steuerelemente hinzu](#AddControlsToGroups).

   Steuerelemente können nur für Gruppen gelöscht werden. Sie können ein-Steuerelement nicht direkt auf eine Registerkarte oder auf das Menüband ziehen. Gruppen können nur auf Registerkarten abgelegt werden. Sie können eine Gruppe nicht direkt in ein Menüband ziehen.

   Ordnen Sie Steuerelemente durch Ziehen zu den korrekten Positionen an. Sie können die Eigenschaften eines Steuer Elements festlegen, indem Sie das **Eigenschaften** Fenster verwenden.

   Sie können Steuerelemente nicht von einer Registerkarte auf eine andere Registerkarte im Menüband ziehen. Wenn Sie ein-Steuerelement auf eine andere Registerkarte verschieben möchten, müssen Sie den Befehl " **Ausschneiden** " verwenden, um das Steuerelement aus einer Registerkarte zu entfernen, und dann das Steuerelement auf einer anderen Registerkarte Wenn Sie das Steuerelement Ausschneiden und einfügen, wird der Ereignishandler nicht mehr funktionieren. Sie können den Ereignishandler im **Eigenschaften** Fenster wiederherstellen. Weitere Informationen finden Sie unter [Eigenschaftenfenster](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Hinzufügen benutzerdefinierter Registerkarten zum Menüband
 Es gibt drei Möglichkeiten, dem Menüband eine benutzerdefinierte Registerkarte hinzuzufügen:

- Fügen Sie eine Registerkarte aus der **Toolbox** hinzu.

- Klicken Sie mit der rechten Maustaste auf den Menüband-Designer, und klicken Sie dann auf **Menüband**

- Öffnen Sie den **Registerkarten Sammlungs-Editor**, und klicken Sie dann auf **Hinzufügen**

   Wählen Sie zum Öffnen des Register **Karten** Auflistungs-Editors im Fenster **Eigenschaften** die Eigenschaft **Tabstopps** aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten ![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer").

  Nach dem Hinzufügen einer Registerkarte können Gruppen mit Steuerelementen hinzugefügt werden.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Entfernen von benutzerdefinierten Registerkarten aus dem Menüband
 Es gibt drei Möglichkeiten, eine benutzerdefinierte Registerkarte aus dem Menüband zu entfernen:

- Klicken Sie mit der rechten Maustaste auf den Designer, und klicken Sie dann auf Menü **Band Registerkarte**

- Klicken Sie im Bereich **Befehle** des Fensters **Eigenschaften** auf **Registerkarte des Menübands entfernen**.

- Öffnen Sie den Registerkarten- **Editor**, wählen Sie die Registerkarte aus, und klicken Sie dann auf **Entfernen**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Ändern der Position einer Registerkarte im Menüband
 Sie können die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern. Sie können auch benutzerdefinierte Registerkarten vor oder nach einer integrierten Registerkarte im Menüband positionieren. Weitere Informationen finden Sie unter Gewusst [wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Anpassen integrierter Registerkarten auf dem Menüband
 Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office Anwendung befindet. Beispielsweise ist die Registerkarte " **Daten** " eine integrierte Registerkarte in Excel.

 Sie können einer integrierten Registerkarte Gruppen und Steuerelemente hinzufügen. Standardmäßig wird eine benutzerdefinierte Gruppe auf einer integrierten Registerkarte als letzte Gruppe angezeigt, Sie können Sie jedoch vor oder nach einer beliebigen integrierten Gruppe auf der Registerkarte verschieben.

 Integrierte Gruppen können nicht entfernt werden.

 Ausführliche Informationen zum Anpassen einer integrierten Registerkarte finden Sie unter Gewusst [wie: Anpassen einer integrierten Register](../vsto/how-to-customize-a-built-in-tab.md)Karte.

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Hinzufügen von Gruppen zu einer Registerkarte
 Gruppen organisieren Steuerelemente auf dem Menüband logisch. Fügen Sie Registerkarten Gruppen hinzu. Fügen Sie der Gruppe alle anderen Steuerelemente hinzu.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Hinzufügen von Steuerelementen zu Gruppen
 Fügen Sie einer Gruppe mindestens ein Steuerelement hinzu. In der folgenden Tabelle wird jedes Steuerelement beschrieben.

|Control|BESCHREIBUNG|
|-------------|-----------------|
|**Feld**|Ein Container, der Steuerelemente in einer Gruppe organisiert. Sie können einem Feld mit Ausnahme eines Trenn Zeichens, einer Gruppe oder einer Registerkarte ein beliebiges Steuerelement hinzufügen. Ein Feld kann horizontal oder vertikal sein.|
|**Schaltfläche**|Eine Schaltfläche, durch die eine Aktion gestartet wird. Sie können einer Gruppe, einer Schaltflächengruppe, einer Dropdownliste, einem Katalog, einem Menü oder einer Trennschaltfläche eine Schaltfläche hinzufügen.|
|**ButtonGroup**|Eine Gruppe, die mindestens eine Schaltfläche, eine Umschaltfläche, ein Menü, eine Trennschaltfläche und einen Katalog beinhaltet. Einer Gruppe oder einem Menü kann eine Schaltflächengruppe oder eine Gruppe hinzugefügt werden.|
|**CheckBox**|Ein Feld, das zum Aktivieren oder Deaktivieren einer Option aktiviert oder deaktiviert ist.|
|**ComboBox**|Ein Bearbeitungsfeld mit einem angehängten Listenfeld. Benutzer können ihre Auswahl entweder eingeben oder auswählen. Im Feld wird die aktuelle Auswahl angezeigt. Verwenden <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> Sie die-Eigenschaft, um Elemente zur Laufzeit vor oder nach dem Laden des Menübands in die Office-Anwendung hinzuzufügen und zu entfernen.|
|**DropDown**|Eine Liste der Elemente, die von Benutzern ausgewählt werden können. In eine Dropdownliste kann kein neues Element eingegeben werden.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>-Eigenschaft Elemente hinzu. Elemente können während der Laufzeit hinzugefügt und entfernt werden.<br /><br /> Fügen Sie der Liste mithilfe der <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>-Eigenschaft Schaltflächen hinzu. Sie können jedoch keine Schaltflächen zur Laufzeit hinzufügen und entfernen, nachdem das Menüband in die Office-Anwendung geladen wurde.|
|**EditBox**|Ein Feld, in das der Benutzer Text eingeben kann.|
|**Galerie**|Ein Menü mit einem visuellen Auswahlarray oder -raster, in dem Benutzer eine Auswahl treffen können. Das Layout der Auswahl im Menü kann gesteuert werden. Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>-Eigenschaft, um die Anzahl der Zeilen und Spalten anzugeben, in denen die Elemente und Schaltflächen des Katalogs angezeigt werden.|
|**Label**|Text, den Sie verwenden können, um Steuerelemente auf dem Menüband zu identifizieren.|
|**Menü**|Eine Dropdownliste, die sämtliche der folgenden Steuerelemente beinhalten kann:<br /><br /> -Schaltfläche<br />-Kontrollkästchen<br />-Gallery<br />-Menü<br />-Trenn Schaltfläche<br />-UMSCHALT Fläche<br />-Trennzeichen<br /><br /> Wenn Sie einem Menü im Menüband-Designer ein Steuerelement hinzufügen möchten, klicken Sie im Menü auf den Pfeil nach unten, um die Menüentwurfsoberfläche anzuzeigen. Sie können dann Menüband-Steuerelemente aus der **Toolbox** in das Menü ziehen. Ordnen Sie Steuerelemente durch Ziehen zu den gewünschten Positionen an.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>Wenn Sie nach dem Laden des Menübands in die Office-Anwendung Steuerelemente hinzufügen möchten, müssen Sie die- <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> Eigenschaft auf **true** festlegen, bevor das Menüband geladen wird. Weitere Informationen hierzu finden Sie unter Übersicht über das [Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md).|
|**Trennzeichen**|Eine dünne Leiste zum Trennen von Elementen in einer Liste. Beim Hinzufügen zu einer Gruppe ist die Leiste vertikal. Beim Hinzufügen zu einem Menü ist die Leiste horizontal.|
|**SplitButton**|Eine Schaltfläche mit einem angehängten Menü. Eine Trennschaltfläche kann jedes der folgenden Steuerelemente beinhalten:<br /><br /> -Schaltfläche<br />-Kontrollkästchen<br />-Gallery<br />-Menü<br />-Trenn Schaltfläche<br />-UMSCHALT Fläche<br />-Trennzeichen<br /><br /> Ebenso wie das Menü verfügt die Trennschaltfläche über eine eigene Entwurfsoberfläche. Im Gegensatz zu einem Menü können Sie jedoch nur die Elemente in einer Trenn Schaltfläche Aktualisieren, bevor das Menüband in die Office-Anwendung geladen wird. Informationen zum Aktualisieren der Elemente in einer unterteilten Schaltfläche finden Sie unter [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Eine Schaltfläche, die gedrückt oder nicht gedrückt angezeigt wird.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Behandeln von Ereignissen und Festlegen von Eigenschaften
 Mit dem Menüband-Designer können Sie mithilfe des Fensters **Eigenschaften** zur Entwurfszeit Steuerelement Eigenschaften festlegen. Außerdem stellt das Menüband ein stark typisiertes Objektmodell zur Verfügung, mit dem Sie die Eigenschaften von Menü Band Steuerelementen zur Laufzeit erhalten und festlegen können.

 Sie können auf jedes Steuerelement im Designer doppelklicken, um einen Ereignishandler für das Standardereignis des Steuerelements zu öffnen. Sie können Ereignishandler für alle anderen Steuerelement Ereignisse erstellen, indem Sie das **Eigenschaften** Fenster verwenden.

 Menübandereignisse befinden sich im <xref:Microsoft.Office.Tools.Ribbon>-Namespace. Das Element **Menüband (visueller Designer)** fügt dem Projekt automatisch einen Verweis auf diese Assembly hinzu und fügt die entsprechende **using** -oder **Imports** -Anweisung am Anfang der Menüband-Codedatei ein.

 Informationen zum Behandeln von Menü Band Ereignissen und zum Festlegen der Eigenschaften von Menü Band Steuerelementen zur Laufzeit finden Sie unter Übersicht über das [Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md).

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Backstage-Ansicht anpassen
 Mit dem Menüband-Designer können Sie dem Menü Steuerelemente hinzufügen, die geöffnet werden, wenn Sie auf die Registerkarte **Datei** klicken. Dieses Menü wird als Backstage-Ansicht bezeichnet.

 Sie können mit dem Menüband-Designer keine Steuerelemente vor oder nach integrierten Steuerelementen positionieren. Ein integriertes Steuerelement ist ein Steuerelement, das bereits in der Backstage-Ansicht angezeigt wird. Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie ein Menüband-XML verwenden. Weitere Informationen zu **Menüband (XML)** finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md). Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) und [Anpassen der Office 2010-Backstage-Ansicht für Entwickler](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Weitere Informationen zum Hinzufügen von Steuerelementen zur Backstage-Ansicht finden Sie unter Gewusst [wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Barrierefreiheit im Menüband-Designer
 Steuerelemente auf dem Menüband-Designer können mithilfe von Tastenkombinationen verschoben werden. Einige Tastenkombinationen gelten für alle Steuerelemente, wohingegen einige Tastenkombinationen nur für Steuerelemente mit Menüs verwendbar sind.

 Die für alle Steuerelemente verwendbaren Tastenkombinationen werden in der folgenden Tabelle angezeigt.

|Aktion|Tastenkombinationen|
|------------|-----------------------|
|Verschieben eines Steuerelements vor das vorherige Steuerelement in der Liste.|**STRG** + Nach **oben**<br /><br /> **STRG** + **Links**|
|Verschieben eines Steuerelements hinter das nächste Steuerelement in der Liste.|**STRG** + **Nach unten**<br /><br /> **STRG** + **Rechts**|
|Verschieben der Auswahl von einem Steuerelement zu einem anderen Steuerelement in derselben Gruppe. Wechseln Sie in einem Dropdownbereich zwischen dem übergeordneten Steuerelement und den Steuerelementen im Dropdownbereich.|**Up**<br /><br /> **Nach unten**|
|Durchlaufen aller Steuerelemente (vorwärts).|**TABULATORTASTE**|
|Durchlaufen aller Steuerelemente (rückwärts).|**UMSCHALT**+**Tab**|
|Löschen des ausgewählten Steuerelements oder eines Satzes von Steuerelementen.|**Löschen**|
|Kopieren der ausgewählten Steuerelemente.|**STRG** + **C**|
|Ausschneiden der ausgewählten Steuerelemente.|**STRG** + **X**|
|Einfügen von Steuerelementen aus der Zwischenablage.|**STRG** + **V**|
|Wählen Sie den **Werkzeugkasten** aus.|**STRG** + **Alt** + **X**|
|Auswählen der übergeordneten Komponente.|**ESC**|

 Die Tastenkombinationen gelten nur für das Microsoft Office-Menü; <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> und <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> werden in der folgenden Tabelle angezeigt.

|Aktion|Tastenkombinationen|
|------------|-----------------------|
|Auswählen des übergeordneten Steuerelements, falls der Dropdownbereich geöffnet ist und im Dropdownbereich ein Steuerelement ausgewählt ist.|**Left**|
|Schließen des Dropdownbereichs, falls der Dropdownbereich geöffnet ist und das übergeordnete Steuerelement ausgewählt ist.|**Left**|
|Öffnen des Dropdownbereichs.|**Right**|
|Auswählen des ersten Steuerelements im Dropdownbereich, falls der Dropdownbereich geöffnet ist.|**Right**|
|Schließen eines Dropdownbereichs.|**ESC**|

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
