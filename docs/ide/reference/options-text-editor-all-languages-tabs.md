---
title: Optionen, Text-Editor, Alle Sprachen, Tabstopps
description: Hier erfahren Sie, wie Sie mit der Seite „Registerkarten“ im Abschnitt „Alle Sprachen“ das Standardverhalten der Registerkarten des Code-Editors in Visual Studio ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c429b8e6dbf6931ebf68717b6d43fcf746cf13ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905557"
---
# <a name="options-text-editor-all-languages-tabs"></a>Optionen, Text-Editor, Alle Sprachen, Registerkarten

Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Wählen Sie zum Anzeigen dieser Optionen unter **Tools** den Menüpunkt **Optionen** aus. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Tabstopps** aus.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die Tabstopp-Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen in „Text-Editor“ für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

Wenn auf den Optionsseiten von „Tabstopps“ für bestimmte Programmiersprachen andere Einstellungen ausgewählt sind, wird die Meldung „Die Einzugseinstellungen für einzelne Textformate stehen miteinander im Konflikt“ für abweichende Optionen unter **Einzug** angezeigt. Die Meldung „Die Tabstoppeinstellungen für einzelne Textformate stehen miteinander im Konflikt“ wird für unterschiedliche **Tabstopps**-Optionen angezeigt. Diese Erinnerung wird beispielsweise angezeigt, wenn die Option **Intelligenter Einzug** für Visual Basic und **Block indenting** (Blockeinzug) für Visual C++ ausgewählt ist.

## <a name="indenting"></a>Einzug

Keine

Wenn diese Option aktiviert ist, werden neue Zeilen nicht eingezogen. Die Einfügemarke wird in der ersten Spalte einer neuen Zeile platziert.

Blockieren

Wenn diese Option aktiviert ist, werden neue Zeilen automatisch eingezogen. Die Einfügemarke wird am selben Ausgangspunkt wie die vorangehende Zeile platziert.

Intelligent

Wenn diese Option aktiviert ist, werden neue Zeilen mithilfe anderer Codeformateinstellungen und IntelliSense-Konventionen für Ihre Entwicklungssprache entsprechend dem Codekontext positioniert. Diese Option ist nicht für alle Programmiersprachen verfügbar.

Beispielsweise können Zeilen, die zwischen einer öffnenden geschweiften Klammer ( { ) und einer schließenden geschweiften Klammer ( } ) eingeschlossen sind, automatisch um einen zusätzlichen Tabstopp von der Position der ausgerichteten Klammern aus eingezogen werden.

## <a name="tabs"></a>Registerkarten

Tabulatorgröße

Legt den Abstand zwischen den Tabstopps fest. Der Standardwert ist vier Leerzeichen.

Einzugsgröße

Legt die Größe des automatischen Einzugs in Leerzeichen fest. Der Standardwert ist vier Leerzeichen. Es werden entweder Tabstopps, Leerzeichen oder beides verwendet, um den angegebenen Raum zu füllen.

Leerzeichen einfügen

Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen nur Leerzeichen und keine Tabstoppzeichen eingefügt. Wenn beispielsweise die **Indent size** (Größe des Einzugs) auf 5 festgelegt wird, werden jedes Mal fünf Leerzeichen eingefügt, wenn Sie die TAB-TASTE drücken oder auf der Symbolleiste **Format** auf die Schaltfläche **Einzug vergrößern** klicken.

Tabulatoren beibehalten

Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen so viele Tabstoppzeichen wie möglich eingefügt. Jedes Tabstoppzeichen füllt die in **Tabstoppgröße** angegebene Anzahl von Leerzeichen auf. Wenn **Indent size** kein ganzzahliges Vielfaches von **Tabstoppgröße** ist, werden Leerzeichen hinzugefügt, um den Unterschied auszugleichen.

## <a name="see-also"></a>Siehe auch

- [Optionen, Text-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)
- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
