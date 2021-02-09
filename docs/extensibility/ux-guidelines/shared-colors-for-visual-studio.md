---
title: Freigegebene Farben für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe allgemeiner Visual Studio-shellelemente und-Designs ihre eigene benutzerdefinierte Benutzeroberfläche entwerfen, die mit der Visual Studio-Umgebung konsistent ist.
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 856f071cbab3156daa6afd0a5282a69636f2fe8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927222"
---
# <a name="shared-colors-for-visual-studio"></a>Freigegebene Farben für Visual Studio
Wenn Sie die Benutzeroberfläche entwerfen, die allgemeine Visual Studio-shellelemente verwendet, oder wenn Sie möchten, dass das Schnittstellen Element mit ähnlichen Features konsistent ist, verwenden Sie vorhandene Tokennamen in Paket Definitions Dateien, um Farben auszuwählen und zuzuweisen. Dadurch wird sichergestellt, dass Ihre Benutzeroberfläche mit der gesamten Visual Studio-Umgebung konsistent ist und automatisch angepasst wird, wenn Designs hinzugefügt oder aktualisiert werden.

In diesem Artikel werden allgemeine Elemente der Benutzeroberfläche und die jeweils verwendeten Tokennamen beschrieben, auf die Sie bei der Erstellung einer ähnlichen Benutzeroberfläche verweisen können. Spezielle Informationen zum Zugriff auf diese Farbtoken finden Sie unter [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Stellen Sie sicher, dass Sie die Tokennamen ordnungsgemäß verwenden:

- **Verwenden Sie Tokennamen nach Funktion und nicht nach Farbe.** Die gemeinsam verwendeten Farben sind bestimmten Benutzeroberflächenelementen zugeordnet und sollten ausschließlich für gleiche oder ähnliche Features verwendet werden. Beispielsweise sollten Sie die Farbe eines gedrückten Kombinationsfelds nicht für eine animierte drehende Statusanzeige verwenden, nur weil Ihnen die Farbe gefällt. Die Funktionen des Kombinations Felds und der Animation sind unterschiedlich, und wenn sich die dem Kombinations Feld zugeordnete Farbe ändert, ist Sie möglicherweise nicht mehr für Ihr Animations Element geeignet. Die konsistente Verwendung von Farben bietet den Benutzern eine Orientierungshilfe und schließt Verwechslungen aus.

- **Verwenden Sie Hintergrund- und Textfarben in der richtigen Kombination.** Den Hintergrundfarben, die für die Verwendung mit Text vorgesehen sind, ist eine Textfarbe zugeordnet. Verwenden Sie keine anderen als die für diesen Hintergrund angegebenen Textfarben. Wenn keine zugeordnete Textfarbe vorhanden ist, sollten Sie diese Hintergrundfarbe nicht für eine Oberfläche verwenden, auf der Sie den Text anzeigen möchten. Andere Kombinationen aus Text-und Hintergrundfarben können zu einer nicht lesbaren Schnittstelle führen.

- **Verwenden Sie Steuerelementfarben, die für die jeweilige Position geeignet sind.** In bestimmten Zuständen haben einige Visual Studio-Steuerelemente keine separaten Rahmen-und Hintergrundfarben. Stattdessen werden diese Farben von den dahinter liegenden Oberflächen übernommen. Stellen Sie sicher, dass Sie für die Position, an der Sie das Steuerelement platzieren, immer geeignete Tokennamen verwenden.

> [!IMPORTANT]
> Verwenden Sie keine Token, die in den Kategorien "Start Seite" oder "Cider" gefunden wurden.

## <a name="common-shared-controls"></a>Gemeinsam verwendete Steuerelemente

Wenn Sie in ihrer Funktion eine standardmäßige Visual Studio-Befehlsleiste verwenden, haben Sie Zugriff auf formatierte Shell-Steuerelemente. Sie sollten diese allgemeinen Steuerelemente nicht neu erstellen. Wenn Sie jedoch eine benutzerdefinierte Befehlsleiste erstellen müssen, kann es erforderlich sein, benutzerdefinierte Steuerelemente zu erstellen. Stellen Sie in diesem Fall sicher, dass Sie die richtigen Tokennamen für jedes der folgenden Steuerelemente verwenden, damit die Benutzeroberfläche mit den anderen Bereichen von Visual Studio konsistent ist.

### <a name="button-controls"></a>Schaltflächen-Steuerelemente

![Button-Steuerelement (rote Linie)](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Schaltflächen im Dokument, die Sie in Visual Studio-Themen integrieren möchten (hell, dunkel, blau oder System hoher Kontrast Design). | ... für Schaltflächen, die für einen benutzerdefinierten Hintergrund angezeigt werden, der nicht Teil eines Visual Studio-Designs ist. |

**Schaltfläche: Standardstatus**

![Standard Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. Standard")<br />Standard Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.Button` |
| Schaltflächenrahmen | `CommonControls.ButtonBorder` |

**Schaltfläche: Standardstatus**

![Standard Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. Default")<br />Standard Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDefault` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDefault` |

**Schaltfläche: deaktivierter Zustand**

![Schaltfläche deaktiviert](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. deaktiviert")<br />Schaltfläche deaktiviert

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonDisabled` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderDisabled` |

**Schaltfläche: Hover-Zustand**

![Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. Hover")<br />Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonHover` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderHover` |

**Schaltfläche: gedrückter Zustand**

![Gedrückte Schaltfläche](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. gedrückt")<br />Gedrückte Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonPressed` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderPressed` |

**Schaltfläche: Fokus Zustand**

![Schaltfläche mit Fokus](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button. Fokus")<br />Schaltfläche mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Schaltfläche | `CommonControls.ButtonFocused` |
| Schaltflächenrahmen | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrollkästchen-Steuerelemente
![Kontrollkästchen (Redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Kontrollkästchen (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Kontrollkästchen-Steuerelemente, die im Dokument gut enthalten sind. | ... für alle Benutzeroberflächen, die kein Kontrollkästchen-Steuerelement sind. |

**Kontrollkästchen: Standardstatus**

![Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Standard Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackground` |
| Rahmen | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Kontrollkästchen: deaktivierter Zustand**

![Deaktiviertes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Deaktiviertes Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundDisabled` |
| Rahmen | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Kontrollkästchen: Hover-Zustand**

 ![Kontrollkästchen, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Kontrollkästchen, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundHover` |
| Rahmen | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Kontrollkästchen: gedrückter Zustand**

![Gedrücktes Kontrollkästchen](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Gedrücktes Kontrollkästchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Rahmen | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Kontrollkästchen: Fokus Zustand**

![Kontrollkästchen für Fokus](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Kontrollkästchen für Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundFocused` |
| Rahmen | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Dropdown-und Kombinations Felder
![Dropdown-/Kombinations Feld (Redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Dropdown-/Kombinations Feld (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Dropdown Listen und Kombinations Felder im Dokument. | ... für alle Benutzeroberflächen, die keine Dropdown-oder Kombinations Felder sind. |
| | ... für [Dropdown-](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) oder Kombinations [Felder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)in der Befehlsleiste. |

**Dropdown-und Kombinations Felder: Standardstatus**

![Standard-Dropdown Feld/Kombinations Feld](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Standard-Dropdown Feld/Kombinations Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackground` |
| Rahmen | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Trennzeichen | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackground` |

**Dropdown-und Kombinations Felder: deaktivierter Zustand**

![Deaktiviertes Dropdown/Kombinations Feld](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Deaktiviertes Dropdown/Kombinations Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundDisabled` |
| Rahmen | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Dropdown-und Kombinations Felder: Hover-Zustand**

![Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Dropdown-/Kombinationsfeld, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundHover` |
| Rahmen | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Dropdown-und Kombinations Felder: gedrückter Zustand**

![Gedrücktes Dropdown/Kombinations Feld](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Gedrücktes Dropdown/Kombinations Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundPressed` |
| Rahmen | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Dropdown Listen und Kombinations Felder Listenelement Ansicht: gedrückter Zustand**

 ![Dropdown-/Kombinations Feld: Listenelement Ansicht](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Dropdown-/Kombinations Feld: Listenelement Ansicht

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Elementtext | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Hintergrundschatten | `CommonControls.ComboBoxListBackgroundShadow` |

**Dropdown-und Kombinations Felder: Fokus Zustand**

![Dropdown-/Kombinations Feld mit Fokus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Dropdown-/Kombinations Feld mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.ComboBoxBackgroundFocused` |
| Rahmen | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Trennzeichen | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Glyphenhintergrund | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Dropdown-und Kombinations Felder: Texteingabe Auswahl**

![Dropdown-/Kombinations Feld-Texteingabe Auswahl](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Dropdown-/Kombinations Feld-Texteingabe Auswahl

| Element | Tokenname: Category.color |
| --- | --- |
| Markierung | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tabellendaten-Steuerelemente (Raster)
Tabellendaten-Steuerelemente, die auch als Rastersteuerelemente bezeichnet werden. Dies sind gebräuchliche Steuerelemente in Visual Studio, die werden verwendet, um große Datenmengen in mehreren Spalten darzustellen. Standardmäßige Tabellendaten-Steuerelemente sind in Visual Studio an mehreren Orten zu finden: z. a. in Fehlerlisten-Toolfenstern, IntelliTrace-Berichte und Speicherheapansichten. Verwenden Sie immer die standardmäßig bereitgestellten Tabellendaten-Steuerelemente. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die standardmäßigen Tabellendaten-Steuerelemente. Verwenden Sie in dieser Situation die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Tabellendaten-Steuerelementen in Visual Studio konsistent ist.

![Tabellarisches Daten/Raster-Steuerelement (Redline)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabellarisches Daten/Raster-Steuerelement (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für tabellarische oder Raster Steuerelemente. | ... für alle Benutzeroberflächen, die kein tabellarisches oder Raster Steuerelement sind. |

#### <a name="column-headers"></a>Spaltenüberschriften
Spaltenheader setzen sich aus Hintergrund, Rahmen, Titeltext und einer optionalen Glyphe zusammen, die normalerweise verwendet wird, wenn ein Raster nach dieser Spalte sortiert wird.

**Spalten Kopfzeile: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.Default` |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Header.Glyph` |
| Rahmen | `Header.SeparatorLine` |

**Spalten Kopfzeile: Hover-Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Header.MouseOver` |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Header.MouseOverGlyph` |
| Rahmen | `Header.SeparatorLine` |

**Spalten Kopfzeile: gedrückter Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `CommonControls.CheckBoxBackgroundPressed` |
| Vordergrund (Text) | `CommonControls.CheckBoxBorderPressed` |
| Vordergrund (Glyphe) | `CommonControls.CheckBoxTextPressed` |
| Rahmen | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Listenansichtselemente
 Listenansichtselemente bestehen aus einem Hintergrund und dem Inhalt. Der Inhalt kann Text, ein Symbol oder beides sein.

**Listen Ansichts Elemente: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Transparent |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | Keine |

**Listen Ansichts Elemente: aktiver Status**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActiveText` |
| Rahmen | Keine |

**Listen Ansichts Elemente: inaktiver Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactiveText` |
| Rahmen | Keine |

### <a name="ui-text"></a>UI-Text

#### <a name="instructional-text"></a>Anweisungs Text
Der Anweisungs Text bietet eine wichtige Erläuterung, was auf einer Dialogfeld-oder Dokument Seite zu tun ist.

![Standardmäßiger Anweisungs Text](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Standardmäßiger Anweisungs Text

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundär Anweisungs Text
In Dokument Seiten mit vielen Text-und Steuerelementen verwendet ein Anweisungs Text einen anderen Farbwert. Auf diese Weise können Sie übermitteln, welche Informationen am wichtigsten sind, und die Gesamtdichte der Benutzeroberflächen Elemente verringern. (Siehe auch den nachfolgenden Abschnitt zu Hinweis Text.)

![Sekundär Anweisungs Text](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundär Anweisungs Text

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Hinweis Text
Der Hinweis Text wird in einem leeren Steuerelement, unterhalb eines Steuer Elements oder auf einer leeren Dokument Oberfläche angezeigt, um dem Benutzer anzuzeigen, was als Nächstes geschehen soll. Sie können den Hinweis Text entweder mit dem Fenster oder dem Steuerelement Hintergrund verwenden.

**Standard Hinweis Text**

![Standard Hinweis Text](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Standard Hinweis Text

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlEditHintText` |

**Erforderlicher Hinweis Text**

![Erforderlicher Hinweis Text](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Erforderlicher Hinweis Text

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.ControlRequiredHintText` |
| Hintergrund | `Environment.ControlRequiredBackground` |

**Textfeld-Steuerelement Text**

> Weitere Farb Token im Zusammenhang mit dem Such Steuerelement finden Sie unter [Suchfelder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) .

![Textfeld-Steuerelement Text](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Textfeld-Steuerelement Text

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Der Hyperlink ist ein Steuerelement, das kein Vordergrund-/hintergrundpaar hat. Verwenden Sie in allen Fällen die Vordergrund-Linkfarbe, die in dunklen, grauen und weißen Hintergründen ordnungsgemäß angezeigt wird. Wenn Sie das farbtoken für das Link Steuerelement nicht verwenden, wird die Standardsystem Farbe für "gedrückt" angezeigt, die rot blinkt. Das ist das Signal, dass das Steuerelement nicht das richtige Umgebungs Farb Token verwendet.

![Hyperlink (Redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hyperlink (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie einen benutzerdefinierten Link erstellen müssen. | ... für alles, was kein Hyperlink ist. |

**Hyperlink: Standardstatus**

![Standard Hyperlink](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Standard Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlink` |

**Hyperlink: Hover-Zustand**

![Hyperlink, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hyperlink, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkHover` |

**Hyperlink: gedrückter Zustand**

![Gedrückter Hyperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Gedrückter Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkPressed` |

**Hyperlink: Zustand "deaktiviert"**

![Deaktivierter Hyperlink](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Deaktivierter Hyperlink

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Info leisten
Infoleisten werden verwendet, um weitere Informationen zu einem bestimmten Kontext bereitzustellen. Sie erscheinen immer im oberen Bereich eines Dokument- oder Toolfensters.

![Info Leiste (Redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Info Leiste (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen benutzerdefinierter infobars. | ... für Benutzeroberflächen Elemente, die nicht mit einer Info Leiste vergleichbar sind. |

**Info Leiste: Standardstatus**

![Standard Infoleiste](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Standard Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.InfoBarBackground` |
| Vordergrund (Text) | `InfoBar.InfoBar` |
| Rahmen | `InfoBar.InfoBarBorder` |

**Infobar Close ( &times; )-Schaltfläche: Standardstatus**

![Schaltfläche zum Schließen der Standard Infoleiste ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Schaltfläche zum Schließen der Standard Infoleiste ( &times; )

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButton` |
| Rahmen | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Infobar Close ( &times; )-Schaltfläche: Hover-Zustand**

![&times;Schaltfläche zum Schließen der Infoleiste () bei Hover](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />&times;Schaltfläche zum Schließen der Infoleiste () bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonHover` |
| Rahmen | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Infobar Close ( &times; )-Schaltfläche: gedrückter Zustand**

![Schaltfläche zum Schließen der Infoleiste ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Schaltfläche zum Schließen der Infoleiste ( &times; )

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.CloseButtonDown` |
| Rahmen | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Link Schaltfläche für Infobar: Standardstatus**

![Standardlink Schaltfläche für Info Leiste](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Standardlink Schaltfläche für Info Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Link Schaltfläche für Infobar: Hover-Zustand**

![Link Schaltfläche für Infobar bei Hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Link Schaltfläche für Infobar bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit Unterstreichung) |

**Link Schaltfläche für Infobar: gedrückter Zustand**

![Link Schaltfläche für gedrücktes](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Link Schaltfläche für gedrücktes

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit Unterstreichung) |

**Inline Hyperlink der Infobar (innerhalb eines Satzes): Standardstatus**

![Standardlink Schaltfläche für Inline-Info Leiste](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Standardlink Schaltfläche für Inline-Info Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `InfoBar.Hyperlink` |

**Info Leiste Inline Hyperlink (innerhalb eines Satzes): Hover-Zustand**

![Schaltfläche zum Inline Hyperlink der Infobar bei Hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Schaltfläche zum Inline Hyperlink der Infobar bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseOver`<br />(Mit Unterstreichung) |

**Inline Hyperlink der Infobar (innerhalb eines Satzes): gedrückter Zustand**

![Schaltfläche zum Inline-Link auf der Infoleiste](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Schaltfläche zum Inline-Link auf der Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Infobar.HyperlinkMouseDown`<br />(Mit Unterstreichung) |

**Infobar-Schaltfläche: Standardstatus**

![Standardmäßige Info Leiste-Schaltfläche](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Standardmäßige Info Leiste-Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.Button` |
| Vordergrund (Text) | `InfoBar.Button` |
| Rahmen | `InfoBar.ButtonBorder` |

**Infobar-Schaltfläche: Hover-Zustand**

![Infobar-Schaltfläche bei Hover](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Infobar-Schaltfläche bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseOver` |
| Vordergrund (Text) | `InfoBar.ButtonMouseOver` |
| Rahmen | `InfoBar.ButtonMouseOverBorder` |

**Infobar-Schaltfläche: gedrückter Zustand**

![Schaltfläche für gedrückte Info Leiste](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Schaltfläche für gedrückte Info Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonMouseDown` |
| Vordergrund (Text) | `InfoBar.ButtonMouseDown` |
| Rahmen | `InfoBar.ButtonMouseDownBorder` |

**Infobar-Schaltfläche: deaktivierter Zustand**

![Deaktivierte Info Leiste](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Deaktivierte Info Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonDisabled` |
| Vordergrund (Text) | `InfoBar.ButtonDisabled` |
| Rahmen | `InfoBar.ButtonDisabledBorder` |

**Infobar-Schaltfläche: Fokus Zustand**

![Schaltfläche mit Fokus-Infoleiste](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Schaltfläche mit Fokus-Infoleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `InfoBar.ButtonFocus` |
| Vordergrund (Text) | `InfoBar.ButtonFocus` |
| Rahmen | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Bildlaufleisten
Bild Lauf leisten werden von der Visual Studio-Umgebung formatiert und müssen nicht mit einem Design versehen werden. Sie können jedoch entscheiden, dass Sie die in Scrollleisten verwendeten Farben nutzen möchten, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent erscheint.

![Bild Lauf Leiste (rote Linie)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Bild Lauf Leiste (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie eine Benutzeroberfläche erstellen, die mit Visual Studio-Bild Lauf leisten verglichen werden soll. | ... für alles, was Sie nicht immer mit der Bild Lauf leisten-Benutzeroberfläche vergleichen möchten. |

**Scrollleiste: Standardstatus**

![Standard Scrollleiste](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Standard Scrollleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbBackground` |

**Bild Lauf Leiste: Hover-Zustand**

![Bildlaufleiste, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Bildlaufleiste, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbMouseOverBackground` |

*Scrollleiste: gedrückter Zustand**

![Gedrückte Scrollleiste](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Gedrückte Scrollleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Bildlaufleiste | `Environment.ScrollBarBackground` |
| Vordergrund (Ziehpunkt) | `Environment.ScrollBarThumbPressedBackground` |

**ScrollBar-Pfeil: Standardstatus**

![Standard Schiebe leisten Pfeil](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Standard Schiebe leisten Pfeil

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowBackground`<br />(Auf die gleiche Farbe wie die Bild Lauf Leiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyph` |

**ScrollBar-Pfeil: Hover-Zustand**

![Bildlaufleiste (Pfeil), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Bildlaufleiste (Pfeil), wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowMouseOverBackground`<br />(Auf die gleiche Farbe wie die Bild Lauf Leiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**ScrollBar-Pfeil: gedrückter Zustand**

![Pfeil der Bild Lauf Leiste](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Pfeil der Bild Lauf Leiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ScrollBarArrowPressedBackground`<br />(Auf die gleiche Farbe wie die Bild Lauf Leiste festgelegt.) |
| Vordergrund (Glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Suchfelder
Verwenden Sie nach Möglichkeit das allgemeine Suchsteuerelement, das von der Visual Studio-Umgebung bereitgestellt wird. Suchfeldfarben befinden sich in der Kategorie "SearchControl" der Datei **ShellColors.pkgdef** . Diese Datei enthält Tokennamen für Eingabefeld, Aktionsschaltfläche, Dropdown-Schaltfläche und Dropdownmenü.

Ein Suchfeld kann einen von mehreren Zuständen aufweisen, von denen sich einige gegenseitig ausschließen:

- "Mit Fokus" oder "Ohne Fokus" bezieht sich darauf, ob sich der Cursor im Textfeld befindet oder nicht.

- "Aktiv" oder "Inaktiv" bezieht sich darauf, ob der Benutzer eine Suchabfrage in das Textfeld eingegeben hat.

- "Darauf zeigen" bedeutet, dass der Benutzer mit der Maus auf das Suchfeld zeigt (durch diesen Zustand werden alle anderen Zustände überschrieben).

- "Deaktiviert" bedeutet, dass die Suchfunktion für den aktuellen Kontext deaktiviert ist.

![Suchfeld (rote Linie)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Suchfeld (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Entwerfen eines benutzerdefinierten Suchfelds. | ... für alles, was kein Suchfeld ist. |
| | ... für alle Elemente, die nicht immer mit der Such Feld Benutzeroberfläche verglichen werden sollen. |

**Eingabefeld für die Suche nach Fokus**

![Eingabefeld für die Suche nach Fokus](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Eingabefeld für die Suche nach Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedBackground` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | `SearchControl.FocusedBorder` |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Ohne Fokus, aktives Sucheingabe Feld**

![Suche (Eingabefeld) ohne Fokus](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Ohne Fokus, aktives Sucheingabe Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.SearchActiveBackground` |
| Vordergrund (Text) | `SearchControl.SearchActiveBackground` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Nicht fokussiertes, inaktives Sucheingabe Feld**

![Nicht fokussiertes, inaktives Sucheingabe Feld](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nicht fokussiertes, inaktives Sucheingabe Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Unfocused` |
| Vordergrund (Text) | `SearchControl.Unfocused` |
| Rahmen | `SearchControl.UnfocusedBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Hervorgehobene Sucheingabe Feld (nur Text)**

![Hervorgehobene Sucheingabe Feld](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Hervorgehobene Sucheingabe Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Selection` |
| Vordergrund (Text) | `SearchControl.FocusedBackground` |
| Rahmen | Keine |
| Trennzeichen | `SearchControl.FocusedDropDownSeparator` |

**Deaktiviertes Sucheingabe Feld**

![Deaktiviertes Sucheingabe Feld](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Deaktiviertes Sucheingabe Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.Disabled` |
| Vordergrund (Text) | `SearchControl.Disabled` |
| Rahmen | `SearchControl.DisabledBorder` |
| Trennzeichen | `SearchControl.DropDownSeparator` |

**Schaltfläche mit Fokus auf Suchaktion**

![Suche (Aktionsschaltfläche) mit Fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Schaltfläche mit Fokus auf Suchaktion

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | – |

**Schaltfläche für die Suchaktion ohne Fokus**

![Schaltfläche für die Suchaktion ohne Fokus](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Schaltfläche für die Suchaktion ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe "Suchen") | `SearchControl.SearchGlyph` |
| Vordergrund (Glyphe "Beenden") | `SearchControl.StopGlyph` |
| Vordergrund (Glyphe "Löschen") | `SearchControl.ClearGlyph` |
| Rahmen | – |

**Schaltfläche zum Durchsuchen der Aktion**

![Schaltfläche zum Durchsuchen der Aktion](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Schaltfläche zum Durchsuchen der Aktion

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.ActionButtonMouseDown` |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Rahmen | `SearchControl.ActionButtonMouseDownBorder` |

**Schaltfläche zum Deaktivieren der Suchaktion**

![Suche (Aktionsschaltfläche), deaktiviert](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Schaltfläche zum Deaktivieren der Suchaktion

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Rahmen | Keine |

**Dropdown Schaltfläche für fokussierte Suche**

![Dropdown Schaltfläche für fokussierte Suche](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Dropdown Schaltfläche für fokussierte Suche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.FocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.FocusedDropDownButtonBorder` |

**Dropdown Schaltfläche für die Suche ohne Fokus**

![Dropdown Schaltfläche für die Suche ohne Fokus](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Dropdown Schaltfläche für die Suche ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.UnfocusedDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Rahmen | `SearchControl.UnfocusedDropDownButtonBorder` |

**Dropdown Schaltfläche für gedrückte Suche**

![Dropdown Schaltfläche für gedrückte Suche](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Dropdown Schaltfläche für gedrückte Suche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.MouseDownDropDownButton` |
| Vordergrund (Glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Rahmen | `SearchControl.MouseDownDropDownButtonBorder` |

**Dropdown Schaltfläche für deaktivierte Suche**

![Dropdown Schaltfläche für deaktivierte Suche](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Dropdown Schaltfläche für deaktivierte Suche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Rahmen | Keine |

#### <a name="search-drop-down-lists"></a>Dropdownlisten im Suchfeld
Das Dropdown Menü Suchfeld ist möglicherweise etwas komplexer als andere Dropdown Menüs in Visual Studio. Die Abschnitte "Empfohlene Suchvorgänge" und "Suchoptionen" können einzeln oder im Menü angezeigt werden, und jede einzelne ist separat gefärbt. Die beiden Bereiche werden außerdem durch eine Linie getrennt, wenn sie zusammen auftreten, und das gesamte Dropdownmenü ist von einem Rahmen umgeben.

![Dropdown Liste suchen (Redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Dropdown Liste suchen (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen einer benutzerdefinierten Suchdropdown Liste. | ... für Dropdown Listen, die in anderen Kontexten angezeigt werden. |
| ... die richtigen Tokennamen für die richtigen Listen Komponenten. | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Dropdown Listenelemente suchen**

| Element | Tokenname: Category.color |
| --- | --- |
| Rahmen | `SearchControl.PopupBorder` |
| Trennzeichen | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Empfohlene Suchvorgänge: Standardstatus**

![Standardmäßige Empfohlene suchen](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Standardmäßige Empfohlene suchen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupItemText` |

**Empfohlene Suchvorgänge: Hover-Zustand**

![Empfohlene Suchvorgänge bei Hover](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Empfohlene Suchvorgänge bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `SearchControl.PopupMouseOverItemText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: Standardstatus**

![Kontrollkästchen "Suche"](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Standard Suchoptionen (Kontrollkästchen)

![Suchoptionen](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Standard Suchoptionen (Link)

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonText` |
| Headerhintergrund | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Headertext) | `SearchControl.PopupSectionHeaderText` |

**Suchoptionen: Hover-Zustand**

![Suchoptionen (Kontrollkästchen) bei Hover](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Suchoptionen (Kontrollkästchen) bei Hover

![Suchoptionen (Link) beim Hover](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Suchoptionen (Link) beim Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |
| Rahmen | `SearchControl.PopupControlMouseOverBorder` |

**Suchoptionen: gedrückter Zustand**

![Gedrückte Suchoptionen (Kontrollkästchen)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Gedrückte Suchoptionen (Kontrollkästchen)

![Gedrückte Suchoptionen (Link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Gedrückte Suchoptionen (Link)

| Element | Tokenname: Category.color |
| --- | --- |
| Kontrollkästchen-Hintergrund | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Kontrollkästchentext) | `SearchControl.PopupCheckboxMouseDownText` |
| Linkhintergrund | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Linktext) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Struktur Ansichten
Mehrere Tool Fenster, einschließlich der Projektmappen-Explorer, Server-Explorer und Klassenansicht, implementieren ein hierarchisches Organisationsschema, dessen Farben über Farbnamen in der Kategorie gesteuert werden `TreeView` . Alle Elemente in einer Strukturansicht haben Hintergrund- und Textfarben. Elemente mit geschachtelten untergeordneten Elementen verfügen außerdem über Glyphen, die anzeigen, ob das Element erweitert oder reduziert ist.

![Strukturansicht (Redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Strukturansicht (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... überall, wo Sie eine hierarchische Organisations Ansicht implementieren müssen. | ... für alle Elemente, die mit einer Strukturansicht nicht vergleichbar sind. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Struktur Ansichts Element: Standardstatus**

![Standardstruktur Ansichts Element](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Standardstruktur Ansichts Element

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.Glyph` |
| Rahmen | Keine |

**Struktur Ansichts Element: Hover-Zustand**

![Struktur Ansichts Element bei Hover](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Struktur Ansichts Element bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.Background` |
| Vordergrund (Text) | `TreeView.Background` |
| Vordergrund (Glyphe) | `TreeView.GlyphMouseOver` |
| Rahmen | Keine |

**Struktur Ansichts Element: ziehen Sie den Zustand.**

![Struktur Ansichts Element bei Drag over](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Struktur Ansichts Element bei Drag over

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.DragOverItem` |
| Vordergrund (Text) | `TreeView.DragOverItem` |
| Vordergrund (Glyphe) | `TreeView.DragOverItemGlyph` |
| Rahmen | Keine |

**Struktur Ansichts Element: ausgewählt, Fokus Zustand**

![Ausgewähltes und fokussiertes Struktur Ansichts Element](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Ausgewähltes und fokussiertes Struktur Ansichts Element

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Struktur Ansichts Element: ausgewählt, Status ohne Fokus**

![Ausgewähltes und nicht fokussiertes Struktur Ansichts Element](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Ausgewähltes und nicht fokussiertes Struktur Ansichts Element

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Rahmen | Keine |

**Struktur Ansichts Element: mit dem Mauszeiger, ausgewählt und fokussiertem Zustand**

![Ausgewähltes und fokussiertes Struktur Ansichts Element bei Hover](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Ausgewähltes und fokussiertes Struktur Ansichts Element bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive` |
| Vordergrund (Text) | `TreeView.SelectedItemActive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | `TreeView.FocusVisualBorder` |

**Struktur Ansichts Element: gepoolt, ausgewählt und ohne Fokus**

![Ausgewähltes und nicht fokussiertes Struktur Ansichts Element bei Hover](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Ausgewähltes und nicht fokussiertes Struktur Ansichts Element bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive` |
| Vordergrund (Text) | `TreeView.SelectedItemInactive` |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Rahmen | Keine |

## <a name="shell-appearance"></a>Shell-Darstellung

### <a name="background"></a>Hintergrund
Der Umgebungshintergrund setzt sich aus zwei Ebenen zusammen. Die untere Ebene ist eine Volltonfarbe, die die gesamte IDE abdeckt. Die obere Ebene befindet sich unterhalb der Befehlsablage und zwischen den automatisch ausgeblendeten Kanälen des Toolfensters am linken und rechten Rand der IDE. Die obere und untere Hintergrund Ebene werden im hellen und dunklen Design auf dieselbe Farbe festgelegt.

![Visual Studio Shell-Hintergrund (Redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio Shell-Hintergrund (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Orte, an denen der Hintergrund der Visual Studio-Umgebung angepasst werden soll. | ... als Füllung für Orte, die keine Hintergrund Oberflächen sind. |
| | ... als Hintergrund für das Platzieren von Vordergrund Elementen. |

**Shelldarstellung der untersten Ebene**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackground` |

**Shelldarstellung der obersten Schicht**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Befehlsablage
Für die Hintergründe der Befehlsablage werden zwei Sätze von Tokennamen verwendet: einer für die Position der Menüleiste und der andere für die Position der Befehlsleisten. Eine einzelne Befehlszeilengruppe verfügt über eigene Hintergrund-Farbwerte, die im Abschnitt "Befehlsleiste" ausführlicher erörtert werden. Menü- und Befehlsleistentext wird in den entsprechenden Abschnitten zur Menü- und Befehlsleiste erörtert.

![Visual Studio-Befehls Regal (Redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio-Befehls Regal (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Bereiche, in denen Menüs oder Symbolleisten platziert werden. | ... für Bereiche, die mit einem Befehls Regal nicht vergleichbar sind. |
|... mit der richtigen Kombination aus Hintergrund-/vordergrundtokenname. | |

**Befehls Regal-Menüleiste**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Befehlsleiste für Befehls Regal**

> Im hellen und dunklen Design von Visual Studio 2013 auf denselben Farbwert festgelegte Farbverlaufsstopps

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest-Designer
Der Manifest-Designer dient dazu, die Bearbeitung der Manifestdatei in Windows 8- und Windows Phone 8-Projekten zu vereinfachen. Obwohl es kein gemeinsames Framework gibt, kann es von Vorteil sein, das Entwurfslayout und die Farben von Ausrichtungs-/Navigationsregisterkarten und Gesamtstruktur aufeinander abzustimmen. Weitere Informationen zu Layoutdetails finden Sie unter [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest-Designer (Redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest-Designer (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Designer, die dem Manifest-Designer ähneln. | ... Wenn Sie über mehr als sechs Registerkarten verfügen. |
| ... anstelle von allgemeinen Registerkarten-Steuerelementen, die im oberen Bereich eines Editors im Dokumentbereich verwendet werden. | ... für jede Benutzeroberfläche, die nicht wie der Manifest-Designer strukturiert ist. |

**Manifest-Designer hat Registerkarte ausgewählt: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.TabActive` |
| Rahmen | Keine |

**Im Manifest-Designer ausgewählter Beschreibungs Bereich: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.DescriptionPane` |

**Ausgewählte Inhaltsseite des Manifest-Designers: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Background` |
| Dialogfeld-Hilfetext | `ManifestDesigner.WatermarkText`<br />(Dieser Tokenname stimmt nicht mit seiner Funktion.) |

**Registerkarte "Manifest-Designer": nicht ausgewähltes Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Inactive` |

**Registerkarte Manifest-Designer: Hover-Zustand**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Befehlsstrukturen

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Kreiert
Menüs können an mehreren Stellen in Visual Studio vorkommen: in der Hauptmenüleiste, eingebettet in Dokument-oder Tool Fenster, oder wenn Sie mit der rechten Maustaste an verschiedenen Positionen in der gesamten IDE klicken. Die Implementierungen von Menüs, die anderen Benutzeroberflächenelementen zugeordnet sind, werden im Abschnitt des entsprechenden Elements erläutert. Sie sollten immer die von der Visual Studio-Umgebung bereitgestellte Standardmenüimplementierung verwenden. In einigen seltenen Fällen haben Sie jedoch möglicherweise keinen Zugriff auf die Visual Studio-Standardmenüs. Verwenden Sie in diesen Situationen die folgenden Tokennamen, um sicherzustellen, dass die Benutzeroberfläche mit anderen Menüs in Visual Studio konsistent ist.

![Visual Studio-Menü (Redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio-Menü (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie ein benutzerdefiniertes Menü erstellen müssen.| ... allein die Hintergrundfarbe. Verwenden Sie immer die angegebene Kombination aus Hintergrund-/Vordergrundfarbe. |
| ... Wenn Sie über eine neue Benutzeroberflächen Komponente verfügen, die mit den Visual Studio-Menüs verglichen werden soll.| |

#### <a name="menu-titles"></a>Menü Titel
Menütitel bestehen aus einem Hintergrund, einem Rahmen und dem Titeltext sowie einer optionalen Glyphe, die normalerweise für Menüs in einer Befehlsleiste verwendet wird.

![Menütitel (Redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menütitel (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... jedes Mal, wenn Sie einen benutzerdefinierten Menütitel erstellen. | ... für alle Elemente, die Sie nicht immer mit dem Menütitel vergleichen möchten. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Menütitel: Standardstatus**

![Standardmenü Titel](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Standardmenü Titel

![Standardmenü Titel mit Glyphe](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Standardmenü Titel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuGlyph` |
| Rahmen | Keine |

**Menütitel: Hover-Zustand**

![Menütitel, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Menütitel, wenn darauf gezeigt wird

![Menütitel mit Glyphe, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Menütitel mit Glyphe, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |

**Menütitel: gedrückter Zustand**

![Gedrückter Menütitel](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Gedrückter Menütitel

![Gedrückter Menütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Gedrückter Menütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder`<br />(Nur Links, obere und Rechte Seite.) |

**Menütitel: deaktivierter Zustand**

![Deaktivierter Menütitel mit Glyphe](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Deaktivierter Menütitel mit Glyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | Keine |

#### <a name="menu-items"></a>Menüelemente
Ein einzelnes Menüelement besteht aus dem Menütext und optional einem Symbol, einem Kontrollkästchen oder einer Untermenü-Glyphe. Hintergrund- und Textfarbe ändern sich, wenn Sie darauf zeigen. Dieses Farbtoken ist eine Kombination aus Hintergrund-/Vordergrundfarbe.

![Menüelemente (rote Linie)](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Verwenden Sie... | Nicht verwenden... |
|---|---|
| ... für alle Dropdown Listen, die von einer Menüleiste oder Befehlsleiste aus gestartet werden. | ... für alle Dropdown Listen in einem anderen Kontext. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Menü Elemente: Standardstatus**

![Standardmenü Elemente](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Standardmenü Elemente

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Rahmen | `Environment.CommandBarMenuBorder` |
| Symbolkanal-Hintergrund | `Environment.CommandBarMenuIconBackground` |
| Trennzeichen | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Menü Elemente: aktiviert und ausgewählte Zustände**

![Menü, aktiviert](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Aktiviertes Menü Element

![Menü, ausgewählt](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Ausgewähltes Menü Element

| Element | Tokenname: Category.color |
| --- | --- |
| Häkchen | `Environment.CommandBarCheckBox` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarSelected` |
| Symbolrahmen | `Environment.CommandBarSelectedBorder` |

**Menü Elemente: Hover-Zustand**

![Menü, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Menü Element bei Hover

![Menü, wenn darauf gezeigt wird (aktiviert)](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Aktiviertes Menü Element bei Hover

![Menü, wenn darauf gezeigt wird (ausgewählt)](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Ausgewähltes Menü Element bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMenuItemMouseOver` |
| Vordergrund (Text) | `Environment.CommandBarMenuItemMouseOverText` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxMouseOver` |
| Häkchenhintergrund | `Environment.CommandBarHoverOverSelectedIcon` |
| Symbolhintergrund | `Environment.CommandBarHoverOverSelected` |
| Symbolrahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menü Elemente: deaktivierter Zustand**

![Menü, deaktiviert](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Deaktiviertes Menü Element

![Menü, deaktiviert (geprüft)](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Deaktiviertes Menü Element mit Häkchen

| Element | Tokenname: Category.color |
| --- | --- |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Vordergrund (Untermenü-Glyphe) | `Environment.CommandBarMenuSubmenuGlyph` |
| Häkchen | `Environment.CommandBarCheckBoxDisabled` |
| Häkchenhintergrund | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Befehlsleisten
Eine Befehlsleiste kann an mehreren Stellen in der Visual Studio-IDE angezeigt werden, insbesondere in der Befehls Ablage und eingebettet in Tool-oder Dokument Fenster.

Generell sollte die von der Visual Studio-Umgebung bereitgestellte Befehlsleisten-Standardimplementierung verwendet werden. Der Standardmechanismus stellt sicher, dass alle visuellen Details ordnungsgemäß angezeigt werden und sich interaktive Elemente konsistent mit anderen Steuerelementen der Visual Studio-Befehlsleiste verhalten. Wenn Sie jedoch eine eigene Befehlsleiste erstellen müssen, ist darauf zu achten, sie anhand der folgenden Tokennamen passend zu gestalten.

![Befehlszeile (rote Linie)](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Befehlsleiste (Redline)

![Schaltfläche "Überlauf" (rote Linie)](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Überlauf Schaltfläche (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... an Stellen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standard Implementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann. | ... für Benutzeroberflächen Elemente, die nicht mit einer Befehlsleiste vergleichbar sind. |
| | ... für andere Befehls leisten Komponenten als diejenigen, für die Tokennamen angegeben werden. |

#### <a name="command-bar-groups"></a>Befehls leisten Gruppen
Eine Befehlsleistengruppe besteht aus einer Gruppe verwandter Befehlsleisten-Steuerelemente und kann eine beliebige Anzahl von Schaltflächen, unterteilten Schaltflächen, Dropdownmenüs, Kombinationsfeldern oder Menüs enthalten. Die Farben dieser Steuerelemente lassen sich anhand separater Tokennamen unterscheiden und werden an anderer Stelle in dieser Anleitung einzeln erörtert. Eine Trennlinie wird verwendet, um eine Befehlsleistengruppe in verwandte Untergruppen aufzuteilen.

![Befehlszeilengruppe (rote Linie)](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Befehls leisten Gruppe (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... an Stellen, an denen eine eingebettete Befehlsleiste benötigt wird, die Standard Implementierung der Visual Studio-Befehlsleiste jedoch nicht verwendet werden kann. | ... für Benutzeroberflächen Elemente, die nicht mit einer Befehlsleiste vergleichbar sind. |
| | ... für andere Befehls leisten Komponenten als diejenigen, für die Tokennamen angegeben werden. |

**Befehls leisten Gruppe: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Rahmen | `Environment.CommandBarToolBarBorder` |
| Ziehpunkt | `Environment.CommandBarDragHandle` |
| Trennzeichen | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Befehlssymbole
![Rote Linie – Befehlssymbol](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Befehls Symbol (Redline)

![Befehls Symbol mit Text Redline](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Befehls Symbol mit Text (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für alle Schaltflächen, die auf einer Befehlsleiste platziert werden. | ... für Steuerelemente mit eigenen Tokennamen. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Befehls Symbol: Standardstatus**

![Standardmäßiges Befehlssymbol](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Standard Befehls Symbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Rahmen | – |

**Befehls Symbol: Standardstatus, ausgewählt**

![Standard, ausgewähltes Befehls Symbol](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Standard, ausgewähltes Befehls Symbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextSelected` |
| Rahmen | `Environment.CommandBarSelectedBorder` |

**Befehls Symbol: hover-oder Fokus Zustände**

![Befehls Symbol bei Hover oder Fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Befehls Symbol bei Hover oder Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehls Symbol: hover-oder Fokus Zustände, ausgewählt**

![Ausgewähltes Befehls Symbol bei Hover oder Fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ausgewähltes Befehls Symbol bei Hover oder Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarHoverOverSelected` |
| Vordergrund (Text) | `Environment.CommandBarTextHoverOverSelected` |
| Rahmen | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Befehls Symbol: gedrückter Zustand**

![Gedrücktes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Gedrücktes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Rahmen | `Environment.CommandBarBorder` |

**Befehls Symbol: deaktivierter Zustand**

![Deaktiviertes Befehlssymbol](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Deaktiviertes Befehlssymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Text) | `Environment.CommandBarTextInactive` |
| Rahmen | – |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Kombinations Felder der Befehlsleiste

> [!IMPORTANT]
> Kombinationsfelder ähneln Dropdowns, enthalten im Unterschied dazu jedoch einen bearbeitbaren Textbereich. Wenn die Dropdown Liste keinen bearbeitbaren Textbereich enthält, verwenden Sie die Farb Token für die [Dropdown Liste der Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Kombinations Feld "Befehlsleiste" (rote Linie)](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Kombinations Feld "Befehlsleiste" (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Aufbau benutzerdefinierter Kombinations Felder. | ... Wenn Sie nicht möchten, dass Sie immer mit der Befehls leisten-Benutzeroberfläche in Einklang stehen. |
| ... beim Erstellen eines Befehls leisten-Steuer Elements, das einem Kombinations Feld ähnelt. | ... Wenn Sie Zugriff auf ein formatiertes Kombinations Feld haben. |

**Eingabefeld für Kombinations Feld der Befehlsleiste: Standardstatus**

![Eingabefeld für Kombinations Feld der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Eingabefeld für Kombinations Feld der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxBackground` |
| Vordergrund (Text) | `Environment.ComboBoxText` |
| Rahmen | `Environment.ComboBoxBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Standardstatus**

![Kombinations Feld, Dropdown&#45;Schaltfläche](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Dropdown-Schaltfläche der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | N/V (erbt vom Befehlsleisten-Hintergrund) |
| Vordergrund (Glyphe) | `Environment.ComboBoxGlyph` |

**Befehls leisten-Dropdown Liste: Standardstatus**

![Befehls leisten-Dropdown Liste](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Befehls leisten-Dropdown Liste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxPopupBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.ComboBoxPopupBorder` |

**Eingabefeld für Kombinations Feld der Befehlsleiste: Hover-Zustand**

![Eingabefeld für Kombinations Feld der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Eingabefeld für Kombinations Feld der Befehlsleiste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxMouseOverText` |
| Rahmen | `Environment.ComboBoxMouseOverBorder` |
| Trennzeichen | `Environment.ComboBoxMouseOverSeparator` |

 **Dropdown-Schaltfläche der Befehlsleiste: Hover-Zustand**

![Dropdown Schaltfläche für Befehls leisten-Kombinations Feld bei Hover](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Befehls leisten-Dropdown-Schaltfläche bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Befehls leisten-Dropdown Liste: Hover-Zustand**

 ![Dropdown Liste der Kombinations Felder der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Befehls leisten-Dropdown Liste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Eingabefeld für Kombinations Feld der Befehlsleiste: Fokus Zustand**

![Eingabefeld für das Kombinations Feld für die Befehlsleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Eingabefeld für das Kombinations Feld für die Befehlsleiste mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedBackground` |
| Vordergrund (Text) | `Environment.ComboBoxFocusedText` |
| Rahmen | `Environment.ComboBoxFocusedBorder` |
| Trennzeichen | `Environment.ComboBoxFocusedButtonSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: Fokus Zustand**

![Dropdown Schaltfläche für eine fokussierte Befehlsleiste](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Dropdown Schaltfläche für eine fokussierte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxFocusedButtonBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Eingabefeld für Kombinations Feld der Befehlsleiste: gedrückter Zustand**

![Eingabefeld für das Kombinations Feld "gedrückt" der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Eingabefeld für das Kombinations Feld "gedrückt" der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxMouseDownBackground` |
| Vordergrund (Text) | `Environment.ComboBoxMouseDownText` |
| Rahmen | `Environment.ComboBoxMouseDownBorder` |
| Trennzeichen | `Environment.ComboBoxMouseDownSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: gedrückter Zustand**

![Dropdown Schaltfläche für das Kombinations Feld der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Dropdown Schaltfläche für gedrückte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Eingabefeld für Kombinations Feld der Befehlsleiste: deaktivierter Zustand**

![Eingabefeld für das deaktivierte Befehls leisten-Kombinations Feld](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Eingabefeld für das deaktivierte Befehls leisten-Kombinations Feld

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ComboBoxDisabledBackground` |
| Vordergrund (Text) | `Environment.ComboBoxDisabledText` |
| Rahmen | `Environment.ComboBoxDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: deaktivierter Zustand**

![Dropdown Schaltfläche für deaktiviertes Kombinations Feld der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Dropdown Schaltfläche für deaktivierte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Dropdown in der Befehlsleiste

> [!IMPORTANT]
> Dropdowns ähneln Kombinationsfeldern, enthalten im Unterschied dazu jedoch keinen bearbeitbaren Textbereich. Wenn die Dropdown Liste einen bearbeitbaren Textbereich enthält, verwenden Sie die Farb Token für Befehls leisten-Kombinations [Felder](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Befehls leisten-Dropdown (Redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Befehls leisten-Dropdown (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen benutzerdefinierter Dropdown Listen-Steuerelemente. | ... für alle Elemente, die mit einer Dropdown Liste nicht vergleichbar sind. |
| | ... für Kombinations Felder oder Trenn Schaltflächen. |

**Dropdown-Auswahlfeld der Befehlsleiste: Standardstatus**

![Standard-Dropdown-Auswahlfeld für die Befehlsleiste](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Standard-Dropdown-Auswahlfeld für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownBackground` |
| Vordergrund (Text) | `DropDownText` |
| Rahmen | `DropDownBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: Standardstatus**

![Dropdown Schaltfläche "Standard Befehlsleiste"](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Dropdown Schaltfläche "Standard Befehlsleiste"

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Glyphe) | `Environment.DropDownGlyph` |

**Befehls leisten-Dropdown Liste: Standardstatus**

![Standard Befehlsleiste-Dropdown Liste](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Standard Befehlsleiste-Dropdown Liste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownPopupBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.ComboBoxItemText` |
| Rahmen | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Dropdown-Auswahlfeld der Befehlsleiste: Hover-Zustand**

![Dropdown-Auswahlfeld der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Dropdown-Auswahlfeld der Befehlsleiste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.DropDownMouseOverText` |
| Rahmen | `Environment.DropDownMouseOverBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseOverSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: Hover-Zustand**

![Befehls leisten-Dropdown-Schaltfläche bei Hover](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Befehls leisten-Dropdown-Schaltfläche bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseOverGlyph` |

**Befehls leisten-Dropdown Liste: Hover-Zustand**

![Befehls leisten-Dropdown Liste bei Hover](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Befehls leisten-Dropdown Liste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Menüelement) | `Environment.ComboBoxItemMouseOverBackground` |
| Vordergrund (Text) | `Environment.ComboBoxItemMouseOverText` |
| Rahmen (Menüelement) | `Environment.ComboBoxItemMouseOverBorder` |

 **Dropdown-Auswahlfeld der Befehlsleiste: gedrückter Zustand**

![Dropdown&#45;Dropdown Auswahlfeld gedrückt](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Gedrücktes Dropdown-Auswahlfeld der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownMouseDownBackground` |
| Vordergrund (Text) | `Environment.DropDownMouseDownText` |
| Rahmen | `Environment.DropDownMouseDownBorder` |
| Trennzeichen | `Environment.DropDownButtonMouseDownSeparator` |

**Dropdown-Schaltfläche der Befehlsleiste: gedrückter Zustand**

![Dropdown Schaltfläche für gedrückte Befehlsleiste](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Dropdown Schaltfläche für gedrückte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DropDownMouseDownGlyph` |

**Dropdown-Auswahlfeld der Befehlsleiste: deaktivierter Zustand**

![Deaktiviertes Dropdown-Auswahlfeld für die Befehlsleiste](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Deaktiviertes Dropdown-Auswahlfeld für die Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DropDownDisabledBackground` |
| Vordergrund (Text) | `Environment.DropDownDisabledText` |
| Rahmen | `Environment.DropDownDisabledBorder` |
| Trennzeichen | Kein Trennzeichen |

**Dropdown-Schaltfläche der Befehlsleiste: deaktivierter Zustand**

![Dropdown Schaltfläche für deaktivierte Befehlsleiste](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Dropdown Schaltfläche für deaktivierte Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Schaltflächen zum Teilen der Befehlsleiste
Unterteilte Schaltflächen haben viele Tokennamen gemeinsam mit anderen Befehlsleisten-Steuerelementen wie Schaltflächen, Menüs und Befehlsleistentext. Alle erforderlichen Tokennamen für Aktions- und Dropdownschaltflächen werden hier wiederholt. Dropdown Listen für unterteilte Schaltflächen sind Implementierungen von [Befehls leisten Menüs](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Trennschaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Geteilte Schaltfläche der Befehlsleiste (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen einer benutzerdefinierten Trenn Schaltfläche. | ... für andere Arten von Schaltflächen. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Trenn Schaltfläche für Befehlsleiste: Standardzustand**

![Standard Befehls leisten-Trenn Schaltfläche](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Standard Befehls leisten-Trenn Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Keine |
| Vordergrund (Text) | `Environment.CommandBarTextActive` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Rahmen | – |
| Trennzeichen | – |

**Befehls leisten-Trenn Schaltfläche: Hover-Zustand**

![Unterteilte Schaltfläche der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Unterteilte Schaltfläche der Befehlsleiste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextHover` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | `Environment.CommandBarSplitButtonSeparator` |

**Geteilte Schaltfläche der Befehlsleiste: gedrückter Zustand**

![Geteilte Schaltfläche der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Geteilte Schaltfläche der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.CommandBarTextMouseDown` |
| Vordergrund (Glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Rahmen | `Environment.CommandBarBorder` |
| Trennzeichen | – |

**Trenn Schaltfläche für Befehlsleiste: deaktivierter Zustand**

![Deaktivierte Schaltfläche der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Deaktivierte Schaltfläche der Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Text) | `Environment.ComboBoxItemTextInactive` |
| Vordergrund (Glyphe) | `Environment.CommandBarTextInactive` |
| Rahmen | – |
| Trennzeichen | – |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Befehlsleiste "Weitere Optionen" und "Überlauf"-Schaltflächen
Die Schaltfläche "Weitere Optionen" wird verwendet, wenn eine Befehlsleistengruppe angepasst werden kann, indem verwandte Befehlsleistenschaltflächen hinzugefügt oder entfernt werden. Die Schaltfläche "Überlauf" wird angezeigt, wenn eine Befehlsleiste aus Platzgründen in horizontaler Richtung abgeschnitten ist. Beim Klicken auf die Schaltfläche wird ein Menü mit den nicht angezeigten Befehlsleisten-Schaltflächen eingeblendet. Die Farben dieser beiden Schaltflächen werden über dieselbe Gruppe von Tokennamen gesteuert.

![Schaltfläche "Weitere Optionen" (Redline) der Befehlsleiste](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Schaltfläche "Weitere Optionen" (Redline) der Befehlsleiste

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für benutzerdefinierte Schaltflächen "Weitere Optionen" oder "Überlauf". | ... für Schaltflächen, die nicht über eine ähnliche Funktionalität wie eine Schaltfläche "Weitere Optionen" oder "Überlauf" verfügen. |

**Befehlsleiste "Weitere Optionen" und "Überlauf"-Schaltflächen: Standardstatus**

![Schaltfläche "Weitere Optionen" der Standard Befehlsleiste](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Schaltfläche "Weitere Optionen" der Standard Befehlsleiste

![Schaltfläche "Überlauf" der Standard Befehlsleiste](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Schaltfläche "Überlauf" der Standard Befehlsleiste

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsBackground` |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsGlyph` |

**Befehlsleiste "Weitere Optionen" und "Überlauf"-Schaltflächen: Hover-Zustand**

![Schaltfläche "Weitere Optionen" auf der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Schaltfläche "Weitere Optionen" auf der Befehlsleiste bei Hover

![Schaltfläche "Überlauf" der Befehlsleiste bei Hover](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Schaltfläche "Überlauf" der Befehlsleiste bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Befehlsleiste "Weitere Optionen" und "Überlauf"-Schaltflächen: gedrückter Zustand**

![Schaltfläche "Weitere Optionen" der Befehlsleiste gedrückt](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Schaltfläche "Weitere Optionen" der Befehlsleiste gedrückt

!["Überlauf", aufgerufen](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Schaltfläche "Überlauf" der Befehlsleiste gedrückt

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Dokumentfenster
Dokument Fenster müssen nicht repliziert werden, da Sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Dokumentfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

Wenn Sie Dokument Fenster-farbtoken verwenden, achten Sie darauf, diese nur für ähnliche Elemente und Always in-Paare zu verwenden. Wenn Sie dies nicht tun, erhalten Sie möglicherweise unerwartete Ergebnisse in der Benutzeroberfläche.

### <a name="document-window-frames"></a>Dokument Fensterrahmen
Dokumentfenster können entweder in der IDE angedockt sein oder unverankert als separates Fenster vorkommen. Wenn ein Dokument Fenster außerhalb der IDE schwebt, befindet es sich immer noch in einem Dokument, und es hat Hintergrund-, Rahmen-, Text-und Registerkarten Farben, die identisch sind, wenn es Teil der IDE ist. Das Dokument ist jedoch von einem Rahmen umgeben, der über eigene Hintergrund-, Rahmen- und Textfarben verfügt. Wenn Toolfenster im Dokumentursprung angedockt sind, erben die enthaltenen Registerkarten ihr Verhalten und ihre Farbe von den Tokennamen des Dokumentfensters.

![Angedocktes Dokument Fenster (rote Linie)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Angedocktes Dokument Fenster (rote Linie)

![Unverankertes Dokument Fenster (rote Linie)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Unverankertes Dokument Fenster (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... an jeder Stelle, an der Sie die Benutzeroberfläche erstellen, die Sie dem Dokument Fenster zuordnen möchten. | ...  für alle Benutzeroberflächen, die nicht automatisch geändert werden sollen, wenn die Shell über ein Design Update verfügt. |

**Angedocktes oder unverankertes Dokument Fenster: Standardstatus**

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | Hängt vom Dokumenttyp ab. |
| Vordergrund (Text) | Hängt vom Dokumenttyp ab. |
| Rahmen | `Environment.ToolWindowBorder` |

**Fokus, unverankertes Dokument Fensterrahmen: Standardstatus**

![Standard Fokus, gleitendes Dokument Fensterrahmen](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Standard Fokus, gleitendes Dokument Fensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrame` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Festgelegt auf transparent) |

**Ohne Fokus, unverankertes Dokument Fensterrahmen: Standardstatus**

![Standard ohne Fokus, unverankertes Dokument Fensterrahmen](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Standard ohne Fokus, unverankertes Dokument Fensterrahmen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Text) | `Environment.ToolWindowFloatingFrameInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Rahmen | `Environment.MainWindowInactiveBorder` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Festgelegt auf transparent) |

**Fokus, unverankerter Dokument Fensterrahmen: Hover-Zustand**

![Fokus, unverankerter Dokument Fensterrahmen bei Hover](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Fokus, unverankerter Dokument Fensterrahmen bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Ohne Fokus, unverankerter Dokument Fensterrahmen: Hover-Zustand**

![Ohne Fokus, unverankerter Dokument Fensterrahmen beim Hover](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Ohne Fokus, unverankerter Dokument Fensterrahmen beim Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Fokus, unverankertes Dokument Fensterrahmen: gedrückter Zustand**

![Fokus, unverankertes Dokument Fensterrahmen beim Drücken](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Fokus, unverankertes Dokument Fensterrahmen beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund (Glyphe) | `Environment.RaftedWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Rahmen (Glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Dokumentregisterkarten
Dokumentregisterkarten befinden sich im Registerkartenkanal und zeigen an, welche Dokumente gerade geöffnet sind und welches das aktuell ausgewählte oder aktive Dokument ist. Toolfenster können ebenfalls im Dokument-Registerkartenkanal angedockt sein, wenn sie vom Benutzer dort platziert werden. In diesem Fall verwenden sie die gleichen Registerkartenfarben wie die Dokumentfenster. Wenn Sie Benutzeroberflächen erstellen, die grundsätzlich auf die Farben des Dokumentfensters abgestimmt sein sollen (einschließlich Designaktualisierungen oder bei Installation neuer Designs), verweisen Sie auf diese Farbtoken.

![Dokument Registerkarten (Redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Dokument Registerkarten (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... an jeder Stelle, an der Sie die Benutzeroberfläche erstellen möchten, die Sie mit Dokument Registerkarten vergleichen und automatisch Design Aktualisierungen oder neue Design Farben auswählen können. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell ein Design Update aufweist. |

#### <a name="open-document-tabs"></a>Geöffnete Dokumentregisterkarten
Jedes geöffnete Dokument verfügt über eine Registerkarte im Dokument-Registerkartenkanal, auf der der Name angezeigt wird. Dokumente können entweder ausgewählt oder im Hintergrund geöffnet sein. Ihre Registerkarten können folgende Zustände haben:

- Die ausgewählte Registerkarte stellt das Dokument dar, das aktuell im Dokumentursprung angezeigt wird. Eine ausgewählte Registerkarte verfügt über einen Dokumentrahmen, der sich über den oberen Rand des Dokumentursprungs erstreckt.

- Hintergrund Registerkarten sind Dokument Registerkarten, die nicht die derzeit ausgewählte Registerkarte sind. Nachdem Sie darauf geklickt haben, werden Sie zur ausgewählten Registerkarte und erhalten alle Hintergrund-, Rahmen-und Textfarben von den Tokennamen.

![Registerkarte "Dokument öffnen" (rote Linie)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Registerkarte "Dokument öffnen" (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen von benutzerdefinierten Dokument Registerkarten. | ... für vorläufige Registerkarten (Vorschau). |
| | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Ausgewählt, Registerkarte mit Fokus**

![Ausgewählt, Registerkarte mit Fokus](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Ausgewählt, Registerkarte mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabSelectedGradientTop`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabSelectedText` |
| Rahmen | `Environment.FileTabSelectedBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabDocumentBorderBackground` |

**Ausgewählte, nicht fokussierte Dokument Registerkarte**

![Ausgewählte, nicht fokussierte Dokument Registerkarte](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Ausgewählte, nicht fokussierte Dokument Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabInactiveGradientTop`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabInactiveText` |
| Rahmen | `Environment.FileTabInactiveBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabInactiveDocumentBorderBackground` |

**Registerkarte "Hintergrunddokument": Standardstatus**

![Standard Registerkarte für das Hintergrunddokument](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Standard Registerkarte für das Hintergrunddokument

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabBackground` |
| Vordergrund (Text) | `Environment.FileTabText` |
| Rahmen | `Environment.FileTabBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

**Registerkarte "Hintergrunddokument": Hover-Zustand**

![Registerkarte "Hintergrunddokument" bei Hover](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Registerkarte "Hintergrunddokument" bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabHotGradientTop`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.FileTabHotText` |
| Rahmen | `Environment.FileTabHotBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

#### <a name="preview-tab"></a>Vorschauregisterkarte
Wird auch als "vorläufige" Registerkarte bezeichnet. Die Registerkarte Vorschau wird auf der rechten Seite des Dokument-Registerkarten Kanals angezeigt, wenn der Benutzer auf ein Element im Projektmappen-Explorer Tool Fenster klickt. Sie fungiert als Dokumentvorschau und gibt dem Benutzer die Möglichkeit, das Dokument auf der linken Seite des Dokument-Registerkartenkanals geöffnet zu lassen. Es kann jeweils nur eine Vorschauregisterkarte geöffnet sein. Vorschauregisterkarten können (wie geöffnete Registerkarten) sowohl im Hintergrund geöffnet als auch ausgewählt sein und im aktiven Zustand mit oder ohne Fokus verfügbar sein.

![Registerkarte "Vorschau" (rote Linie)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Registerkarte "Vorschau" (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie eine vorläufige Vorschau erstellen und möchten, dass ein Element der aktuellen Vorschau der Registerkarten Farbe entspricht. | ... für alle Arten von Dokumenten oder Registerkarten, die nicht vorläufig sind (Vorschau). |
| | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Fokussiert, ausgewählte Vorschau Registerkarte**

![Fokussiert, ausgewählte Vorschau Registerkarte](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Fokussiert, ausgewählte Vorschau Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedActive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Ohne Fokus, ausgewählte Vorschau Registerkarte**

![Ohne Fokus, ausgewählte Vorschau Registerkarte](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Ohne Fokus, ausgewählte Vorschau Registerkarte

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalSelectedInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Dokumentrahmen | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Registerkarte "Hintergrund Vorschau": Standardstatus**

![Standard Registerkarte für Hintergrund Vorschau](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Standard Registerkarte für Hintergrund Vorschau

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalInactive` |
| Vordergrund (Text) | `Environment.FileTabProvisionalInactiveForeground` |
| Rahmen | `Environment.FileTabProvisionalInactiveBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

**Registerkarte "Hintergrund Vorschau": Hover-Zustand**

![Registerkarte "Hintergrund Vorschau" bei Hover](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Registerkarte "Hintergrund Vorschau" bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.FileTabProvisionalHover` |
| Vordergrund (Text) | `Environment.FileTabProvisionalHoverForeground` |
| Rahmen | `Environment.FileTabProvisionalHoverBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

#### <a name="document-overflow-button"></a>Dokumentüberlauf-Schaltfläche
Die Dokumentüberlauf-Schaltfläche wird angezeigt, wenn mindestens ein Dokument geöffnet ist. Ihre Anzeige ist unabhängig davon, ob der vertikale Platz in der aktuellen Konfiguration für alle Dokumentregisterkarten ausreicht. Das Dokument Überlauf-Dropdown Menü, das von den Menü Farben der [Befehlsleiste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) gesteuert wird, zeigt eine Liste aller geöffneten Dokumente an, sowohl sichtbar als auch ausgeblendet, und das Überlauf Symbol ändert sich abhängig davon, ob alle geöffneten Dokumente im Registerkarten Kanal angezeigt werden.

![Dokument Überlauf-Schaltfläche (Redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Dokument Überlauf-Schaltfläche (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Erstellen einer benutzerdefinierten Dokument Überlauf Schaltfläche. | ... für Benutzeroberflächen, die einer Überlauf Schaltfläche nicht ähneln. |
| | ... für Überlauf Schaltflächen der Befehlsleiste. |

**Dokument Überlauf-Schaltfläche: Standardstatus**

![Standardmäßige Dokument Überlauf Schaltfläche](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Standardmäßige Dokument Überlauf Schaltfläche

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Rahmen | – |

**Dokument Überlauf-Schaltfläche: Hover-Zustand**

![Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Dokumentüberlauf-Schaltfläche, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Dokument Überlauf-Schaltfläche: gedrückter Zustand**

![Schaltfläche "Dokument Überlauf" beim Drücken](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Schaltfläche "Dokument Überlauf" beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Vordergrund (Glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Rahmen | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Kennzeichnung (Tagging)
Visual Studio unterstützt Tags, mit deren Hilfe ein Benutzer suchbare Schlüsselwörter für Nachverfolgungszwecke deklarieren kann. Projektleiter und Entwickler können beispielsweise Team Foundation Server (TFS) verwenden, um Arbeitselemente zu kennzeichnen. Die folgenden Tabellen enthalten Farbnamen sowohl für das Tag selbst als auch für die Glyphe "Schließsymbol", die im Zustand "Darauf zeigen" und "Ausgewählt" angezeigt wird.

![Tagging in Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Tagging in Visual Studio (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für die Benutzeroberfläche, die Tagging unterstützt. | ... für jede andere Art von Benutzeroberfläche. |

#### <a name="tags"></a>Tags

**Tag: Standardstatus**

![Standardtag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Standardtag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.Background` |
| Vordergrund (Text) | `Tag.Background` |

**Tag: Hover-Zustand**

![Tag, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.HoverBackground` |
| Vordergrund (Text) | `Tag.HoverBackgroundText` |

**Tag: gedrückter Zustand**

![Gedrücktes Tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Gedrücktes Tag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.PressedBackground` |
| Vordergrund (Text) | `Tag.PressedBackgroundText` |

**Tag: ausgewählter Status**

![Ausgewähltes Tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Ausgewähltes Tag

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.SelectedBackground` |
| Vordergrund (Text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Close ( &times; )-Tagsymbol

**Close ( &times; )-tagglyphe: Standardstatus**

![Standardmäßige Close ( &times; )-tagglyphe](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Standardmäßige Close ( &times; )-tagglyphe

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyph` |

**Close ( &times; )-tagglyphe: Hover-Zustand**

![Close ( &times; )-Tagsymbol bei Hover](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Close ( &times; )-Tagsymbol bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphHover` |
| Rahmen | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; )-tagglyphe: gedrückter Zustand**

![Gedrücktes Close ( &times; )-Tagsymbol](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Gedrücktes Close ( &times; )-Tagsymbol

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagHoverGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagHoverGlyphPressed` |
| Rahmen | `Tag.TagHoverGlyphPressedBorder` |

**Ausgewähltes Tag mit schließende ( &times; ) Glyphe: Standardstatus**

![Ausgewähltes Standard-Tag mit Close ()-Symbol &times;](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Ausgewähltes Standard-Tag mit Close ()-Symbol &times;

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyph` |

**Ausgewähltes Tag mit schließende ( &times; ) Glyphe: Hover-Zustand**

![Ausgewähltes Tag mit "Close ()"-Symbol &times; beim Hover](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Ausgewähltes Tag mit "Close ()"-Symbol &times; beim Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphHoverBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphHover` |
| Rahmen | `Tag.TagSelectedGlyphHoverBorder` |

**Ausgewähltes Tag mit schließende ( &times; ) Glyphe: gedrückter Zustand**

![Ausgewähltes, gedrücktes Tag mit Close ()-Symbol &times;](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Ausgewähltes, gedrücktes Tag mit Close ()-Symbol &times;

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Tag.TagSelectedGlyphPressedBackground` |
| Vordergrund (Glyphe) | `Tag.TagSelectedGlyphPressed` |
| Rahmen | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Toolfenster
Tool Fenster müssen nicht repliziert werden, da Sie von der Visual Studio-Umgebung bereitgestellt werden. Sie können jedoch festlegen, dass die in den Toolfenstern genutzten Farben verwendet werden, damit Ihre Benutzeroberfläche immer mit diesem Teil der Visual Studio-Umgebung konsistent ist.

![Tool Fenster (Redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Tool Fenster (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie die Benutzeroberfläche erstellen, die Sie mit Tool Fenstern vergleichen möchten. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

### <a name="tool-window-frame"></a>Toolfensterrahmen
Toolfenster in Visual Studio werden für viele verschiedene Aufgaben verwendet und können einen von mehreren unterschiedlichen Zuständen annehmen. Wenn ein Toolfenster geöffnet ist, kann es einer der vier Seiten des Dokumentbereichs zugeordnet werden. Toolfenster können auch unverankert sein und sich außerhalb der IDE befinden. In diesem Fall können sie an einer beliebigen Stelle auf dem Benutzerbildschirm positioniert werden. Unverankerte Fenster nehmen immer die höchste Position in der IDE ein. Schließlich können Toolfenster wie Dokumentfenster angedockt und als Registerkarte im Dokumentursprung angezeigt werden. Toolfenster, die als Dokumentfenster angedockt wurden, erhalten ihre Farbe teilweise über die Tokennamen des Dokumentfensters.

![Tool Fensterrahmen (Redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Tool Fensterrahmen (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ...  Wenn Sie die Benutzeroberfläche erstellen, die Sie mit Tool Fenstern vergleichen möchten. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Angedocktes Tool Fenster**

![Angedocktes Tool Fenster](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Angedocktes Tool Fenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.ToolWindowBorder` |

**Unverankertes Tool Fenster**

![Unverankertes Tool Fenster](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Unverankertes Tool Fenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowActiveDefaultBorder` |

**Unverankertes, nicht fokussiertes Tool Fenster**

![Unverankertes, nicht fokussiertes Tool Fenster](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Unverankertes, nicht fokussiertes Tool Fenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowBackground` |
| Rahmen | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Toolbox-ähnliche Fenster
Die Toolbox ist eines der am häufigsten verwendeten Tool Fenster in Visual Studio. Dabei handelt es sich im Wesentlichen um ein Struktur Steuerelement, auf das ein spezielles Design und ein spezielles

![Toolbox ähnliches Fenster (Redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Toolbox ähnliches Fenster (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... beim Entwerfen eines Tool Fensters, das immer mit der shelltoolbox konsistent sein soll. | ... für alle Elemente, die der Toolbox-Benutzeroberfläche nicht ähneln, oder wenn Sie nicht sicher sind, ob Ihre Benutzeroberfläche bei Änderung der shelltoolbox-Farben Probleme haben wird. |

**Toolbox Knoten: Standardstatus**

![Standardmäßiger Toolbox-übergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Standardmäßiger Toolbox-übergeordneter Knoten

![Standardmäßiger Toolbox-untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Standardmäßiger Toolbox-untergeordneter Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContent`<br />He |
| Hintergrund | `Environment.ToolWindowBackground`<br />(Einzelne Elemente oder ganzes Fenster, wenn keine Steuerelemente verfügbar sind) |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `Environment.ToolboxContent` |
| Vordergrund (Text) | `Environment.ToolboxContent` |

**Untergeordnete Toolbox-Knoten: Hover-Zustand**

![Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Toolbox (untergeordneter Knoten), wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolboxContentMouseOver`<br />(Nur einzelne Elemente) |
| Rahmen | Keine |
| Vordergrund (Text) | `Environment.ToolboxContentMouseOver`<br />(Nur einzelne Elemente) |

**Ausgewählte Toolbox Knoten: Fokus Zustand**

![Fokus, ausgewählter Toolbox (übergeordneter Knoten)](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Fokus, ausgewählter Toolbox (übergeordneter Knoten)

![Fokus, ausgewählter Toolbox-untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Fokus, ausgewählter Toolbox-untergeordneter Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | `TreeView.FocusVisualBorder`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Glyphe) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemActive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Ausgewählte Toolbox Knoten: Status ohne Fokus**

![Ausgewählter, nicht fokussierter Toolbox (übergeordneter Knoten)](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Ausgewählter, nicht fokussierter Toolbox (übergeordneter Knoten)

![Ausgewählter, nicht fokussierter Toolbox-untergeordneter Knoten](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Ausgewählter, nicht fokussierter Toolbox-untergeordneter Knoten

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Rahmen | Keine |
| Vordergrund (Glyphe) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Vordergrund (Text) | `TreeView.SelectedItemInactive`<br />Aus Kategorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Titelleiste des Toolfensters
Der Rahmen der Titelleiste ist kein echter Rahmen, sondern eine Dicke Linie über dem oberen Rand der Titelleiste. Er verfügt über keinen Tokennamen für seinen nicht fokussierten Zustand.

![Tool Fenstertitelleiste (Redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Tool Fenstertitelleiste (Redline)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie die Benutzeroberfläche erstellen, die Sie mit Tool Fenstern vergleichen möchten. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Titelleiste mit Fokus**

![Titelleiste mit Fokus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Titelleiste mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarActiveGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarActiveText` |
| Rahmen | `Environment.TitleBarActiveBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |
| Ziehpunkt | `Environment.TitleBarDragHandleActive` |

**Titelleiste ohne Fokus**

![Titelleiste ohne Fokus](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Titelleiste ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.TitleBarInactiveGradientBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.TitleBarInactiveText` |
| Rahmen | – |
| Ziehpunkt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Schaltflächen der Tool Fenster-Titelleiste
![Titelleisten Schaltfläche (rote Linie)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Titelleisten Schaltfläche (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... für Schaltflächen, die in der Benutzeroberfläche angezeigt werden, die farbtoken aus den Titelleisten des Tool Fensters verwendet. | ... für Schaltflächen, die an anderen Speicherorten angezeigt werden. |
| | ... in einer anderen Kombination aus Hintergrund und Vordergrund als angegeben. |

**Titelleisten Schaltflächen mit Fokus: Standardstatus**

![Standard, Titelleisten Schaltflächen mit Fokus](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Standard, Titelleisten Schaltflächen mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Rahmen | – |

**Schaltflächen ohne Fokus in der Titelleiste: Standardzustand**

![Standard, nicht fokussierte Titelleisten Schaltflächen](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Standard, nicht fokussierte Titelleisten Schaltflächen

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | – |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Rahmen | – |

**Titelleisten Schaltflächen mit Fokus: Hover-Zustand**

![Fokus leisten-Schaltflächen auf dem Mauszeiger](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Fokus leisten-Schaltflächen auf dem Mauszeiger

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverActive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverActiveBorder` |

**Titelleisten Schaltflächen ohne Fokus: Hover-Zustand**

![Nicht fokussierte Titelleisten Schaltflächen bei Hover](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Nicht fokussierte Titelleisten Schaltflächen bei Hover

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonHoverInactive` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Titelleisten Schaltflächen mit Fokus: gedrückter Zustand**

![Fokus leisten Schaltflächen beim Drücken](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Fokus leisten Schaltflächen beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

**Titelleisten Schaltflächen ohne Fokus: gedrückter Zustand**

![Nicht fokussierte Titelleisten Schaltflächen beim Drücken](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Nicht fokussierte Titelleisten Schaltflächen beim Drücken

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowButtonDown` |
| Vordergrund (Glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Rahmen | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Toolfenster-Registerkarten
![Registerkarte "Tool Fenster" (rote Linie)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Registerkarte "Tool Fenster" (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie die Benutzeroberfläche erstellen, die Sie mit Tool Fenstern vergleichen möchten. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Ausgewählt, Toolfenster-Registerkarte mit Fokus**

![Ausgewählt, Toolfenster-Registerkarte mit Fokus](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Ausgewählt, Toolfenster-Registerkarte mit Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedActiveText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

**Ausgewählt, Toolfenster-Registerkarte ohne Fokus**

![Ausgewählt, Toolfenster-Registerkarte ohne Fokus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Ausgewählt, Toolfenster-Registerkarte ohne Fokus

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabSelectedTab` |
| Vordergrund (Text) | `Environment.ToolWindowTabSelectedText` |
| Rahmen | `Environment.ToolWindowTabSelectedBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

**Registerkarte des Hintergrund Tool Fensters: Standardstatus**

![Standard Registerkarte für das Hintergrund Tool Fenster](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Standard Registerkarte für das Hintergrund Tool Fenster

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(In Visual Studio 2013 wird der Farbverlaufs Stopp auf denselben Farbwert festgelegt.) |
| Vordergrund (Text) | `Environment.ToolWindowTabText` |
| Rahmen | `Environment.ToolWindowTabBorder` |

**Registerkarte des Hintergrund Tool Fensters: Hover-Zustand**

![Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Hintergrundregisterkarte im Toolfenster, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(In Visual Studio 2013 wird der Farbverlaufs Stopp auf denselben Farbwert festgelegt.) |
| Vordergrund (Text) | `Environment.ToolWindowTabMouseOverText` |
| Rahmen | `Environment.ToolWindowTabMouseOverBorder`<br />(Auf die gleiche Farbe wie der Hintergrund festgelegt.) |

### <a name="auto-hide-tabs"></a>Automatisch ausgeblendete Registerkarten

![Registerkarten automatisch ausblenden (rote Linie)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Registerkarten automatisch ausblenden (rote Linie)

| Verwenden Sie... | Nicht verwenden... |
| --- | --- |
| ... Wenn Sie eine Benutzeroberfläche erstellen, die Sie automatisch ausgeblendeten Tool Fenster Registerkarten zuordnen möchten. | ... für alle Benutzeroberflächen, die Sie nicht automatisch ändern möchten, wenn die Shell über ein Design Update verfügt. |

**Registerkarten automatisch ausblenden: Standardstatus**

![Automatisch ausgeblendete Registerkarte, Standard](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Automatisch ausgeblendete Registerkarte, Standard

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabText` |
| Rahmen | `Environment.AutoHideTabBorder` |

**Registerkarten automatisch ausblenden: Hover-Zustand**

![Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automatisch ausgeblendete Registerkarte, wenn darauf gezeigt wird

| Element | Tokenname: Category.color |
| --- | --- |
| Hintergrund | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Verlaufs Stopps für dieses Token werden nicht in der Benutzeroberfläche verwendet.) |
| Vordergrund (Text) | `Environment.AutoHideTabMouseOverText` |
| Rahmen | `Environment.AutoHideTabMouseOverBorder` |
