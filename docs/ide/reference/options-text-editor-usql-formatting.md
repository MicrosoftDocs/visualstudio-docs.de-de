---
title: Formatierungsoptionen des U-SQL-Editors
description: Hier erfahren Sie, wie Sie über die Seite mit den Formatierungsoptionen und die zugehörigen Unterseiten die Optionen für die Codeformatierung beim Programmieren in U-SQL im Code-Editor festlegen.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf65c6c80bbcf24d48f5da584349cc4d6b26049
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040289"
---
# <a name="options-text-editor-u-sql-formatting"></a>Optionen, Text-Editor, U-SQL, Formatierung

Auf der Optionsseite **Formatierung** können Sie Optionen zur Formatierung von Code im Code-Editor festlegen. Klicken Sie auf **Extras** > **Optionen**, um die Optionsseite aufzurufen. Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor** > **U-SQL** > **Formatierung**.

## <a name="general-page"></a>Seite „Allgemein“

### <a name="general-settings"></a>Allgemeine Einstellungen

Es hängt von den Einstellungen ab, *wann* Formatierungsoptionen für den Code vom Code-Editor übernommen werden.

- **Abgeschlossene Anweisung bei Eingabe eines Semikolons automatisch formatieren**

   Bei Auswahl dieser Option werden Anweisungen nach dem Drücken der SEMIKOLONTASTE entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.

- **Beim Einfügen automatisch formatieren**

   Bei Auswahl dieser Option wird in den Editor eingefügter Text entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.

## <a name="preview-windows"></a>Vorschaufenster

Auf den Unterseiten **Einzug**, **Neue Zeilen**, **Abstand** wird jeweils ein Vorschaufenster im unteren Bereich angezeigt. Im Vorschaufenster wird die Auswirkung der einzelnen Optionen angezeigt. Wählen Sie zur Verwendung des Vorschaufensters eine Formatierungsoption aus. Im Vorschaufenster wird ein Beispiel der ausgewählten Option angezeigt. Wenn Sie eine Einstellung ändern, indem Sie z.B. ein Kontrollkästchen aktivieren oder deaktivieren, wird das Vorschaufenster in Anpassung an diese neue Einstellung aktualisiert.

### <a name="indentation-remarks"></a>Hinweise zu Einzügen

Durch die Einzugsoptionen auf den Seiten **Tabstopps** für die jeweiligen Programmiersprachen wird lediglich festgelegt, an welche Position der Cursor im Code-Editor gesetzt wird, wenn Sie am Ende einer Zeile die **EINGABETASTE** drücken. Die Einzugsoptionen unter **Formatierung** werden angewendet, wenn Code automatisch formatiert wird, z.B.:

- Wenn Sie Code in die Datei einfügen und **Beim Einfügen automatisch formatieren** aktiviert ist
- Wenn der zu formatierende Block manuell eingegeben wird

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Dialogfeld „Optionen“](../../ide/reference/general-environment-options-dialog-box.md)
