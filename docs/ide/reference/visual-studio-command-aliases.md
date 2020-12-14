---
title: Befehlsaliase
description: Hier erfahren Sie, wie Sie Befehlsaliase verwenden, um weniger Zeichen eingeben zu müssen, wenn Sie einen Befehl ausführen möchten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dda564939652a09b64fec65747ca14d1315b3f1
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561070"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Command Aliases

Wenn Sie Befehlsaliasse verwenden, müssen Sie weniger Zeichen eingeben, wenn Sie einen Befehl ausführen. Geben Sie die Aliasse in das Feld **Suchen/Befehl** oder das Fenster **Befehl** ein. Um das Dialogfeld **Datei öffnen** anzuzeigen, können Sie beispielsweise den vordefinierten Alias `>of` verwenden, anstatt `>File.OpenFile` einzugeben.

Geben Sie `alias` in das Fenster **Befehl** ein, um eine Liste der aktuellen Aliasse und ihrer Definitionen anzuzeigen. Geben Sie `>cls` ein, um den Inhalt des **Befehlsfensters** zu löschen. Wenn Sie einen Alias für einen Befehl finden möchten, geben Sie `alias <command name>` ein.

Ein eigener Alias für einen Visual Studio-Befehle lässt sich (mit oder ohne Argumente) leicht erstellen. Beispielsweise lautet die Syntax für Aliasing `File.NewFile MyFile.txt``alias MyAlias File.NewFile MyFile.txt`. Sie können einen Alias mit `alias <alias name> /delete` löschen

In der folgenden Tabelle ist eine Liste der vordefinierten Visual Studio-Befehlsaliase enthalten. Einige Befehlsnamen verfügen über mehr als einen vordefinierten Alias. Klicken Sie auf die Links für die unten folgenden Befehlsnamen, um detaillierte Themen anzuzeigen, in denen die korrekte Syntax sowie die korrekten Argumente und Schalter für diese Befehle erläutert werden.

|Befehlsname|Alias|Vollständiger Name|
|------------------|-----------|-------------------|
|[Befehl "Drucken"](../../ide/reference/print-command.md)|?|Debug.Print|
|[Befehl "Aktuellen Wert anzeigen"](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Hinzufügen eines neuen Projekts|AddProj|File.AddNewProject|
|[Befehl "Alias"](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|Fenster|Autos|Debug.Autos|
|Haltepunkte(Fenster)|bl|Debug.Breakpoints|
|Breakpoint ein/aus|bp|Debug.ToggleBreakPoint|
|Aufruflistenfenster|CallStack|Debug.CallStack|
|Lesezeichen löschen|ClearBook|Edit.ClearBookmarks|
|Schließen|Schließen|File.Close|
|Alle Dokumente schließen|CloseAll|Window.CloseAllDocuments|
|Auswahl aufheben|cls|Edit.ClearAll|
|Befehlsmodus|cmd|View.CommandWindow|
|Code anzeigen|code|View.ViewCode|
|[Befehl "Arbeitsspeicher auflisten"](../../ide/reference/list-memory-command.md)|T|Debug.ListMemory|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) als ANSI|da|Debug.ListMemory /Ansi|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) im Ein-Byte-Format|db|Debug.ListMemory /Format:OneByte|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) als ANSI im Vier-Byte-Format|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) im Vier-Byte-Format|dd|Debug.ListMemory /Format:FourBytes|
|Bis Zeilenanfang löschen|DelBOL|Edit.DeleteToBOL|
|Bis Zeilenende löschen|DelEOL|Edit.DeleteToEOL|
|Horizontalen Leerraum löschen|DelHSp|Edit.DeleteHorizontalWhitespace|
|Sicht-Designer|Designer|View.ViewDesigner|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) im Gleitkommaformat|df|Debug.ListMemory/Format:Float|
|"Disassemblierung" (Fenster)|disasm|Debug.Disassembly|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) im Acht-Byte-Format|dq|Debug.ListMemory /Format:EightBytes|
|[Befehl „Arbeitsspeicher auflisten“](../../ide/reference/list-memory-command.md) als Unicode|du|Debug.ListMemory /Unicode|
|[Befehl "Anweisung auswerten"](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|Schließen|Beenden|File.Exit|
|Auswahl formatieren|format|Edit.FormatSelection|
|Vollbild|FullScreen|View.FullScreen|
|[Befehl "Start"](../../ide/reference/start-command.md)|g|Debug.Start|
|[Gehe zu (Befehl)](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Gehe zu Klammer|GotoBrace|Edit.GotoBrace|
|F1Help|Hilfe|Help.F1Help|
|Unmittelbarer Modus|immed|Tools.ImmediateMode|
|Einfügen einer Datei als Text|InsertFile|Edit.InsertFileAsText|
|[Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|In Kleinbuchstaben umwandeln|Lcase|Edit.MakeLowercase|
|Zeile ausschneiden|LineCut|Edit.LineCut|
|Zeile löschen|LineDel|Edit.LineDelete|
|Member auflisten|ListMembers|Edit.ListMembers|
|Lokalfenster|Locals|Debug.Locals|
|[Befehl "Befehlsfensterausgaben protokollieren"](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|
|Markierungsmodus des Befehlsfensters|markieren|Tools.CommandWindowMarkMode|
|Speicherfenster|Memory Memory1|Debug.Memory1|
|Speicherfenster 2|Memory2|Debug.Memory2|
|Arbeitsspeicherfenster 3|Memory3|Debug.Memory3|
|Arbeitsspeicherfenster 4|Memory4|Debug.Memory4|
|[Befehl "Basis festlegen"](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[Befehl "ShowWebBrowser"](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|Nächstes Lesezeichen|NextBook|Edit.NextBookmark|
|[Befehl "Neue Datei"](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|Neues Projekt|np NewProj|File.NewProject|
|[Open File Command](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|
|[Befehl "Projekt öffnen"](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|Nur Definitionen anzeigen/Gliederung anhalten|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Prozedurschritt|p|Debug.StepOver|
|Parameterinformationen|ParamInfo|Edit.ParameterInfo|
|Rücksprung|pr|Debug.StepOut|
|Vorheriges Lesezeichen|PrevBook|Edit.PreviousBookmark|
|Datei drucken|print|File.Print|
|Eigenschaftenfenster|props|View.PropertiesWindow|
|Beenden|q|Debug.StopDebugging|
|Wiederholen|Wiederholen|Edit.Redo|
|Registerfenster|Register|Debug.Registers|
|Ausführen bis Cursor|rtc|Debug.RunToCursor|
|Ausgewählte Elemente speichern|Speichern|File.SaveSelectedItems|
|Alle speichern|SaveAll|File.SaveAll|
|Speichern unter|SaveAs|File.SaveSelectedItemsAs|
|[Befehl "Shell"](../../ide/reference/shell-command.md)|Shell|Tools.Shell|
|In Dateien suchen beenden|StopFind|Edit.FindInFiles /stop|
|Verankerung vertauschen|SwapAnchor|Edit.SwapAnchor|
|Einzelschritt|t|Debug.StepInto|
|Auswahl mit Tabstopps versehen|Mit Tabstopps versehen|Edit.TabifySelection|
|Aufgabenlistenfenster|TaskList|View.TaskList|
|Threadfenster|Threads|Debug.Threads|
|Untereinander|TileH|Window.TileHorizontally|
|Nebeneinander|TileV|Window.TileVertically|
|Lesezeichen umschalten|ToggleBook|Edit.ToggleBookmark|
|Fenster „Toolbox“|Toolbox|View.Toolbox|
|[Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|In Großbuchstaben umwandeln|Ucase|Edit.MakeUppercase|
|Rückgängig|Rückgängig (undo)|Edit.Undo|
|Tabstopps aus Auswahl entfernen|Tabstopps entfernen|Edit.UntabifySelection|
|Überwachungsfenster|Überwachen|Debug.WatchN|
|Umschalten des Zeilenumbruchs|WordWrap|Edit.ToggleWordWrap|
|Listenprozesse|&#124;|Debug.ListProcesses|
|[Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
