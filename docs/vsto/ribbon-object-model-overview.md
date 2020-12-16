---
title: Übersicht über das Ribbon-Objektmodell
description: Erfahren Sie, wie die Visual Studio-Tools für Office-Laufzeit ein stark typisiertes Objektmodell verfügbar macht, das Sie verwenden können, um die Eigenschaften von Menü Band Steuerelementen zur Laufzeit zu ermitteln und festzulegen
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f97bbbab4b867f503e5b5befff27844df8a4b4bc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527984"
---
# <a name="ribbon-object-model-overview"></a>Übersicht über das Ribbon-Objektmodell
  Der stellt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ein stark typisiertes Objektmodell zur Verfügung, mit dem Sie die Eigenschaften von Menü Band Steuerelementen zur Laufzeit erhalten und festlegen können. Beispielsweise können neue Menüsteuerelemente dynamisch ausgefüllt oder Steuerelemente kontextbezogen angezeigt und ausgeblendet werden. Zudem besteht die Möglichkeit, einem Menüband Registerkarten, Gruppen und Steuerelemente hinzuzufügen. Dies muss jedoch vor dem Laden des Menübands durch die Office-Anwendung erfolgen. Weitere Informationen finden [Sie unter Festlegen von Eigenschaften, die](#SettingReadOnlyProperties)schreibgeschützt werden.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Dieses Menüband-Objektmodell besteht Haupt [](#RibbonClass)sächlich aus der Multifunktionsleistenklasse, Menü [Band Ereignissen](#RibbonEvents)und Menü [Band Steuer](#RibbonControlClasses)Element-Klassen.

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Ribbon-Klasse
 Wenn Sie einem Projekt ein neues Element vom Typ " **Menüband (visueller Designer)** " hinzufügen, fügt Visual Studio dem Projekt eine Menü **Band** Klasse hinzu. Die **Ribbon** -Klasse erbt von der- <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> Klasse.

 Diese Klasse wird als partielle Klasse angezeigt, die zwischen der Menüband-Codedatei und der Codedatei des Menüband-Designers aufgeteilt ist.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Menü Band Ereignisse
 Die Menü **Band** Klasse enthält die folgenden drei Ereignisse:

|Ereignis|BESCHREIBUNG|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wird ausgelöst, wenn die Office-Anwendung die Menü Band Anpassung lädt. Der <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Ereignishandler wird der Menüband-Codedatei automatisch hinzugefügt. Führen Sie beim Laden des Menübands mithilfe dieses Ereignishandlers benutzerdefinierten Code aus.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Ermöglicht das Zwischenspeichern von Bildern in der Menü Band Anpassung beim Laden des Menübands. Sie können einen geringfügigen Leistungsgewinn erzielen, wenn Sie Code schreiben, um die Menüband-Bilder in diesem Ereignishandler zwischenzuspeichern. Weitere Informationen finden Sie unter <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Wird ausgelöst, wenn die Menüband-Instanz geschlossen wird.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Menü Band Steuerelemente
 Der- <xref:Microsoft.Office.Tools.Ribbon> Namespace enthält einen Typ für jedes Steuerelement, das in der Gruppe " **Office-Menüband** -Steuerelemente" der **Toolbox** angezeigt wird.

 In der folgenden Tabelle wird der Typ für jedes `Ribbon`-Steuerelement angezeigt. Eine Beschreibung der einzelnen Steuerelemente finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

|Steuerelementname|Klassenname|
|------------------|----------------|
|**Feld**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Schaltfläche**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galerie**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Gruppieren**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Trennzeichen**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**TABULATORTASTE**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Der <xref:Microsoft.Office.Tools.Ribbon>-Namespace verwendet für diese Typen das Ribbon-Präfix, um einen Namenskonflikt mit den Namen der Steuerelementklassen im <xref:System.Windows.Forms>-Namespace zu verhindern.

 Beim Hinzufügen eines Steuerelements zum Menüband-Designer deklariert der Menüband-Designer die Klasse für dieses Steuerelement als Feld in der Codedatei des Menüband-Designers.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Allgemeine Aufgaben mit den Eigenschaften von Menü Band Steuerelementen
 Jedes `Ribbon`-Steuerelement beinhaltet Eigenschaften, mit denen Sie verschiedene Aufgaben ausführen können, wie das Zuweisen einer Bezeichnung zu einem Steuerelement oder das Ausblenden und Anzeigen von Steuerelementen.

 In einigen Fällen werden Eigenschaften schreibgeschützt, nachdem das Menüband geladen oder ein Steuerelement zu einem dynamischen Menü hinzugefügt wurde. Weitere Informationen finden Sie unter [Festlegen von Eigenschaften, die](#SettingReadOnlyProperties)schreibgeschützt werden.

 In der folgenden Tabelle werden einige der Aufgaben beschrieben, die Sie mithilfe der Eigenschaften des `Ribbon`-Steuerelements ausführen können.

|Aufgabe:|Gehen Sie folgendermaßen vor:|
|--------------------|--------------|
|Aus- oder Einblenden eines Steuerelements.|Verwenden Sie die Visible-Eigenschaft.|
|Aktivieren oder Deaktivieren eines Steuerelements.|Verwenden Sie die aktivierte Eigenschaft.|
|Festlegen der Größe eines Steuerelements.|Verwenden Sie die ControlSize-Eigenschaft.|
|Abrufen des Bilds, das auf einem Steuerelement angezeigt wird.|Verwenden Sie die Image-Eigenschaft.|
|Ändern der Bezeichnung eines Steuerelements.|Verwenden Sie die Label-Eigenschaft.|
|Hinzufügen von benutzerdefinierten Daten zu einem Steuerelement.|Verwenden Sie die Tag-Eigenschaft.|
|Abrufen der Elemente in einem <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>-Steuerelement, einem <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>-Steuerelement oder einem<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>-Steuerelement|Verwenden Sie die Items-Eigenschaft.|
|Hinzufügen eines <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>-Steuerelements, eines <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>-Steuerelements oder eines <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>-Steuerelements.|Verwenden Sie die Items-Eigenschaft.|
|Hinzufügen von Steuerelementen zu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Verwenden Sie die Items-Eigenschaft.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>Wenn Sie nach dem Laden des Menübands in die Office-Anwendung Steuerelemente hinzufügen möchten, müssen Sie die- <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> Eigenschaft auf **true** festlegen, bevor das Menüband in die Office-Anwendung geladen wird. Weitere Informationen finden [Sie unter Festlegen von Eigenschaften, die](#SettingReadOnlyProperties)schreibgeschützt werden.|
|Abrufen des ausgewählten Elements von <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Verwenden Sie die SelectedItem-Eigenschaft. Verwenden Sie für <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> die <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>-Eigenschaft.|
|Abrufen der Gruppen auf <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>-Eigenschaft.|
|Angeben der Anzahl der Zeilen und Spalten, die in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> angezeigt werden.|Verwenden Sie die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>-Eigenschaft und die <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>-Eigenschaft.|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Festlegen von Eigenschaften, die schreibgeschützt werden
 Einige Eigenschaften können nur vor dem Laden des Menübands festgelegt werden. Diese Eigenschaften können an drei Orten festgelegt werden:

- Im **Eigenschaften** Fenster von Visual Studio.

- Im Konstruktor der **Ribbon** -Klasse.

- In der `CreateRibbonExtensibilityObject`-Methode der `ThisAddin`, `ThisWorkbook`- Klasse oder `ThisDocument`-Klasse des Projekts.

  Dynamische Menüs bieten einige Ausnahmen. Sie können neue Steuerelemente erstellen, deren Eigenschaften festlegen und sie dann während der Laufzeit einem dynamischen Menü hinzufügen, und zwar auch nach dem Laden des Menübands mit dem Menü.

  Eigenschaften von Steuerelementen, die Sie einem dynamischen Menü hinzufügen, können jederzeit festgelegt werden.

  Weitere Informationen finden Sie unter [Eigenschaften, die](#ReadOnlyProperties)schreibgeschützt werden.

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Festlegen von Eigenschaften im Konstruktor der Multifunktionsleiste
 Sie können die Eigenschaften eines Steuer Elements `Ribbon` im Konstruktor der **Ribbon** -Klasse festlegen. Dieser Code muss nach dem Aufruf der `InitializeComponent`-Methode angezeigt werden. Im folgenden Beispiel wird einer Gruppe eine neue Schaltfläche hinzugefügt, falls die aktuelle Uhrzeit 17:00 Pacific Time (UTC-8) oder später ist.

 Fügen Sie den folgenden Code hinzu.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 In Visual c#-Projekten, die Sie von Visual Studio 2008 aktualisiert haben, wird der Konstruktor in der Menüband-Codedatei angezeigt.

 In Visual Basic-Projekten oder in Visual C#-Projekten, die Sie in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt haben, wird der Konstruktor in der Menüband-Designer-Codedatei angezeigt. Diese Datei trägt den Namen *yourribbonitem*. Designer.cs oder *yourribbonitem*. Designer. vb. Wenn Sie diese Datei in Visual Basic Projekten anzeigen möchten, müssen Sie zuerst auf die Schaltfläche **alle Dateien anzeigen** in Projektmappen-Explorer klicken.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Festlegen von Eigenschaften in der Methode "kreateribbonextensibilityobject"
 Sie können die Eigenschaften eines `Ribbon`-Steuerelements beim Überschreiben der `CreateRibbonExtensibilityObject`-Methode in der `ThisAddin`-, der `ThisWorkbook`-oder der `ThisDocument`-Klasse des Projekts festlegen. Weitere Informationen zur-Methode finden Sie unter Übersicht über das `CreateRibbonExtensibilityObject` [Menüband](../vsto/ribbon-overview.md).

 Im folgenden Beispiel werden die Menü Band Eigenschaften in der-Methode der- `CreateRibbonExtensibilityObject` `ThisWorkbook` Klasse eines Excel-Arbeitsmappenprojekts festgelegt.

 Fügen Sie den folgenden Code hinzu.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Eigenschaften, die schreibgeschützt werden
 In der folgenden Tabelle werden Eigenschaften angezeigt, die nur festgelegt werden können, bevor das Menüband geladen wird.

> [!NOTE]
> Sie können Sie die Eigenschaften der Steuerelemente in dynamischen Menüs jederzeit festlegen. Diese Tabelle ist in diesem Fall nicht gültig.

|Eigenschaft|Menüband-Steuerelementklasse|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dynamisch**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Gruppen**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Registerkarten**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Titel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Festlegen von Eigenschaften für Menü Bänder, die in Outlook-Inspektoren angezeigt werden
 Bei jedem Öffnen eines Inspektors, in dem das Menüband angezeigt wird, wird eine neue Instanz des Menübands erstellt. Allerdings können die in der Tabelle oben aufgeführten Eigenschaften nur vor dem Erstellen der ersten Instanz des Menübands festgelegt werden. Nach dem Erstellen der ersten Instanz werden diese Eigenschaften schreibgeschützt, da die erste Instanz die XML-Datei definiert, die von Outlook zum Laden des Menübands verwendet wird.

 Sofern Sie über bedingte Logik verfügen, mit der alle diese Eigenschaften auf einen anderen Wert festgelegt werden, wenn andere Instanzen des Menübands erstellt werden, bleibt dieser Code ohne Wirkung.

> [!NOTE]
> Stellen Sie sicher, dass die Eigenschaft **Name** für jedes Steuerelement festgelegt ist, das Sie einem Outlook-Menüband hinzufügen Wenn Sie ein-Steuerelement zur Laufzeit einem Outlook-Menüband hinzufügen, müssen Sie diese Eigenschaft im Code festlegen. Wenn Sie ein-Steuerelement zur Entwurfszeit zu einem Outlook-Menüband hinzufügen, wird die Name-Eigenschaft automatisch festgelegt.

## <a name="ribbon-control-events"></a>Menü Band Steuerungs Ereignisse
 Jede Steuerelementklasse beinhaltet mindestens ein Ereignis. In der folgenden Tabelle werden diese Ereignisse beschrieben.

|Ereignis|BESCHREIBUNG|
|-----------|-----------------|
|Klicken Sie im Menüband auf|Tritt beim Klicken auf ein Steuerelement auf.|
|TextChanged|Tritt beim Ändern des Texts in einem Bearbeitungs- oder Kombinationsfeld auf.|
|ItemsLoading|Tritt auf, wenn die Items-Auflistung des-Steuer Elements von Office angefordert wird. Office speichert die Items-Auflistung zwischen, bis der Code die Eigenschaften des Steuer Elements ändert oder die-Methode aufgerufen wird <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> .|
|ButtonClick|Tritt beim Klicken auf eine Schaltfläche in <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> auf.|
|SelectionChanged|Tritt beim Ändern der Auswahl in <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> oder <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> auf.|
|DialogLauncherClick|Tritt auf, wenn unten rechts in einer Gruppe auf das Symbol für das Dialogfeldstartprogramm geklickt wird.|

 Die Ereignishandler für diese Ereignisse besitzen die folgenden zwei Parameter.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*sen*|Ein <xref:System.Object>, das das Steuerelement darstellt, durch das das Ereignis ausgelöst wurde.|
|*e*|Ein <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>, das ein <xref:Microsoft.Office.Core.IRibbonControl> enthält. Greifen Sie mithilfe dieses Steuerelements auf eine beliebige Eigenschaft zu, die im von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellten Menüband-Objektmodell nicht verfügbar ist.|

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern](../vsto/how-to-show-add-in-user-interface-errors.md)
