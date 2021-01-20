---
title: Optionen, Text-Editor, Allgemein
description: Hier erfahren Sie, wie Sie mit der Seite „Allgemein“ globale Einstellungen für den Code- und Text-Editor von Visual Studio ändern.
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.Advanced
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c76ea1729fa84bee97458f131e18f64281b76567
ms.sourcegitcommit: 4ee20054afe7bcf5c0aed504dec01e18059fbbd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226499"
---
# <a name="options-dialog-box-text-editor--general"></a>Dialogfeld „Optionen“: Text-Editor \> Allgemein

Mit diesem Dialogfeld können Sie Einstellungen für den Code- und -Text-Editor von Visual Studio global ändern. Klicken Sie zum Anzeigen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, und klicken Sie dann auf **Allgemein**.

## <a name="settings"></a>Einstellungen

### <a name="drag-and-drop-text-editing"></a>Textbearbeitung mit Drag & Drop

Bei Auswahl dieser Option können Sie Text verschieben, indem Sie ihn auswählen und mit der Maus auf eine andere Position innerhalb des aktuellen Dokuments oder eines beliebigen anderen geöffneten Dokument ziehen.

### <a name="automatic-delimiter-highlighting"></a>Trennzeichen automatisch hervorheben

Wenn diese Option aktiviert ist, werden die Trennzeichen, die Parameter oder Element-Wert-Paare trennen, sowie übereinstimmende Klammern hervorgehoben.

### <a name="track-changes"></a>Änderungen nachverfolgen

Wenn der Code-Editor ausgewählt ist, erscheint eine vertikale gelbe Linie im Auswahlrand. Diese markiert Code, der seit der letzten Speicherung der Datei geändert wurde. Wenn Sie die Änderungen speichern, wird die vertikale Linie grün.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>UTF-8-Codierung ohne Signatur automatisch erkennen

Standardmäßig erkennt der Editor Codierung durch Suchen nach Bytereihenfolge-Marken oder Charset-Tags. Wenn keines von beidem im aktuellen Dokument gefunden wird, versucht der Code-Editor, UTF-8-Codierung automatisch durch Scannen von Bytefolgen zu erkennen. Deaktivieren Sie diese Option, um die automatische Erkennung der Codierung zu deaktivieren.

### <a name="follow-project-coding-conventions"></a>Codierungskonventionen des Projekts befolgen

Wenn diese Option ausgewählt ist, überschreiben die angegebenen Codierungskonventionen des Projekts alle Codierungskonventionen, die Sie in Ihren persönlichen Projekten verwenden.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Mausklick für den Wechsel zur Definition aktivieren

Wenn diese Option ausgewählt ist, können Sie **STRG** drücken und beim Klicken mit der Maus über ein Element fahren. Dadurch gelangen Sie zur Definition des ausgewählten Elements. Sie können auch entweder **ALT** oder **CTRL** + **ALT** aus der Dropdownliste **Zusatztaste verwenden** auswählen.

Aktivieren Sie das Kontrollkästchen **Definition in der Peek-Ansicht öffnen**, um die Definition des Elements in einem Fenster anzuzeigen, ohne Ihrer aktuellen Position im Code-Editor zu verlassen.

## <a name="display"></a>Anzeige

### <a name="selection-margin"></a>Auswahlrahmen

Wenn diese Option aktiviert ist, wird ein vertikaler Rand am linken Rand des Textbereichs des Editors angezeigt. Sie können auf diesen Rand klicken, um eine ganze Textzeile auszuwählen, oder darauf klicken und ziehen, um aufeinander folgende Textzeilen auszuwählen.

|Auswahlrahmen aktiviert|Auswahlrahmen deaktiviert|
| - | - |
|![HTMLpageSelectionMarginOn-Bildschirmabbildung](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff-Bildschirmabbildung](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Indikatorrand

Wenn diese Option aktiviert ist, wird ein vertikaler Rand außerhalb des linken Randes des Textbereichs des Editors angezeigt. Wenn Sie in diesen Rand klicken, erscheint ein Symbol und eine QuickInfo, die sich auf den angezeigten Text beziehen. Beispielsweise werden im Indikatorrand Verknüpfungen zu Haltepunkt- oder Aufgabenlisten angezeigt. Informationen im Indikatorrand werden nicht gedruckt.

### <a name="highlight-current-line"></a>Aktuelle Zeile markieren

Wenn diese Option aktiviert ist, wird ein grauer Rahmen um die Codezeile angezeigt, in der sich der Cursor befindet.

### <a name="show-structure-guide-lines"></a>Strukturführungslinien anzeigen

Wenn diese Option ausgewählt ist, erscheinen im Editor vertikale Linien, die sich mit strukturierten Codeblöcken decken, sodass Sie die einzelnen Codeblöcke leicht identifizieren können.

### <a name="show-file-health-indicator"></a>Indikator für Dateiintegrität anzeigen

Wenn diese Option aktiviert wird, wird ein Statusindikatorleiste für die Dateiintegrität (Fehler, Warnungen) mit Optionen zur Codebereinigung in der unteren linken Ecke des Editors angezeigt.

## <a name="see-also"></a>Siehe auch

- [Optionen, Text-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)
- [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Optionen, Text-Editor, Dateierweiterung](../../ide/reference/options-text-editor-file-extension.md)
- [Identifizieren und Anpassen von Tastenkombinationen](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Anpassen des Editors](../how-to-change-text-case-in-the-editor.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)
