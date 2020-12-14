---
title: Befehle
description: Hier erfahren Sie mehr über die verschiedenen Befehle, auf die Sie in Visual Studio zugreifen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7928c03e52e4a72fb354bd7202e041ec2264fcd6
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560953"
---
# <a name="visual-studio-commands"></a>Visual Studio-Befehle

Sie können Visual Studio-Befehle im Fenster **Befehl**, im Fenster **Direkt** oder im Feld **Suchen/Befehl** eingeben. In jedem Fall gibt das Größer-als-Zeichen (`>`) an, dass ein Befehl und kein Such- oder Debugvorgang folgt.

Eine vollständige Liste von Befehlen und ihrer Syntax finden Sie auf der Seite **Tastatur** unter **Extras** > **Optionen** > **Umgebung**.

In lokalisierten Versionen der IDE können Befehlsnamen sowohl in der jeweiligen Landessprache der IDE als auch in Englisch eingegeben werden. So können Sie z. B. entweder `File.NewFile` oder `Fichier.NouveauFichier` in der französischen IDE zum Ausführen desselben Befehls eingeben.

Für viele Befehle sind Aliase verfügbar. Eine Liste der Aliase für Befehle finden Sie unter [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md). Tastenkombinationen für Befehle finden Sie unter [Standardtastenkombinationen in Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Escapezeichen

Das Escapezeichen für Visual Studio-Befehle ist ein Caretzeichen (^). Das Escapezeichen bedeutet, dass das unmittelbar darauf folgende Zeichen wörtlich und nicht als Steuerzeichen interpretiert wird. Dies ermöglicht das Einbetten von geraden Anführungszeichen ("), Leerzeichen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter- oder Schalterwert, mit Ausnahme von Schalternamen. Beispiel:

```
>Edit.Find ^^t /regex
```

Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht. Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert.

## <a name="commands-with-arguments"></a>Befehle mit Argumenten

Die folgenden Befehle verwenden Argumente oder Schalter:

| Befehlsname | BESCHREIBUNG |
| - | - |
| [Vorhandenes Element hinzufügen](../../ide/reference/add-existing-item-command.md) | Fügt der aktuellen Projektmappe eine vorhandene Datei hinzu und öffnet diese. |
| [Vorhandenes Projekt hinzufügen](../../ide/reference/add-existing-project-command.md) | Fügt der aktuellen Projektmappe ein vorhandenes Projekt hinzu. |
| [Neues Element hinzufügen](../../ide/reference/add-new-item-command.md) | Fügt der aktuellen Projektmappe ein neues Projektmappenelement wie eine HTM-, CSS-, TXT- oder Framesetdatei hinzu und öffnet dieses. |
| [Alias](../../ide/reference/alias-command.md) | Erstellt einen neuen Alias für einen vollständigen Befehl, einen vollständigen Befehl und seine Argumente oder sogar für einen anderen Alias. |
| [Anweisung auswerten](../../ide/reference/evaluate-statement-command.md) | Wertet die angegebene Anweisung aus und zeigt sie an. |
| [Suchen](../../ide/reference/find-command.md) | Durchsucht Dateien mit einer Teilmenge der Optionen, die auf dem Steuerelement **Suchen und Ersetzen** verfügbar sind. |
| [In Dateien suchen](../../ide/reference/find-in-files-command.md) | Durchsucht Dateien mit einer Teilmenge der Optionen, die auf dem Steuerelement [Suchen in Dateien](../../ide/find-in-files.md). |
| [Gehe zu](../../ide/reference/go-to-command.md) | Bewegt den Cursor in die angegebene Zeile. |
| [Aufrufliste auflisten](../../ide/reference/list-call-stack-command.md) | Zeigt die aktuelle Aufrufliste an. |
| [Disassembly auflisten](../../ide/reference/list-disassembly-command.md) | Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen. |
| [Arbeitsspeicher auflisten](../../ide/reference/list-memory-command.md) | Zeigt den Inhalt des angegebenen Speicherbereichs an. |
| [Module auflisten](../../ide/reference/list-modules-command.md) | Listet die Module für den aktuellen Prozess auf. |
| [Registrierungen auflisten](../../ide/reference/list-registers-command.md) | Zeigt eine Liste mit Registrierungen an. |
| [Quelle auflisten](../../ide/reference/list-source-command.md) | Zeigt die angegebenen Quellcodezeilen an. |
| [Threads auflisten](../../ide/reference/list-threads-command.md) | Zeigt eine Liste der Threads im aktuellen Programm an. |
| [Befehlsfensterausgaben protokollieren](../../ide/reference/log-command-window-output-command.md) | Kopiert die gesamte Ein- und Ausgabe aus dem Befehlsfenster in eine Datei. |
| [Neue Datei](../../ide/reference/new-file-command.md) | Erstellt eine neue Datei und fügt sie dem aktuell ausgewählten Projekt hinzu. |
| [Datei öffnen](../../ide/reference/open-file-command.md) | Öffnet eine vorhandene Datei und ermöglicht die Angabe eines Editors. |
| [Projekt öffnen](../../ide/reference/open-project-command.md) | Öffnet ein vorhandenes Projekt und ermöglicht das Hinzufügen des Projekts zur aktuellen Projektmappe. |
| [Drucken](../../ide/reference/print-command.md) | Wertet den Ausdruck aus und zeigt das Ergebnis oder den angegebenen Text an. |
| [Befehl "Aktuellen Wert anzeigen"](../../ide/reference/quick-watch-command.md) | Zeigt den ausgewählten oder angegebenen Text im Feld **Ausdruck** des Dialogfelds **Schnellansicht** an. |
| [Replace](../../ide/reference/replace-command.md) | Ersetzt Text in Dateien mithilfe einer Teilmenge der Optionen, die auf dem Steuerelement **Suchen und Ersetzen** verfügbar sind. |
| [In Dateien ersetzen](../../ide/reference/replace-in-files-command.md) | Ersetzt Text in Dateien mithilfe einer Teilmenge der Optionen, die unter [In Dateien ersetzen](../../ide/replace-in-files.md). |
| [Aktuellen Stapelrahmen festlegen](../../ide/reference/set-current-stack-frame-command.md) | Ermöglicht die Anzeige eines bestimmten Stapelrahmens. |
| [Aktuellen Thread festlegen](../../ide/reference/set-current-thread-command.md) | Ermöglicht die Anzeige eines bestimmten Threads. |
| [Basis festlegen](../../ide/reference/set-radix-command.md) | Legt die Zahl der anzuzeigenden Bytes fest. |
| [Shell](../../ide/reference/shell-command.md) | Startet Programme in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , als ob der Befehl in der Befehlszeile ausgeführt würde. |
| [Befehl "ShowWebBrowser"](../../ide/reference/showwebbrowser-command.md) | Zeigt die in einem Webbrowserfenster angegebene URL entweder in der integrierten Entwicklungsumgebung (IDE) oder außerhalb der IDE an. |
| [Starten](../../ide/reference/start-command.md) | Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen. |
| [Pfad](../../ide/reference/symbol-path-command.md) | Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht. |
| [Haltepunkt umschalten](../../ide/reference/toggle-breakpoint-command.md) | Schaltet den Haltepunkt entweder ein oder aus, je nach seinem aktuellen Status an der aktuellen Position in der Datei. |
| [Befehl "Überwachung"](../../ide/reference/watch-command.md) | Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . |

## <a name="see-also"></a>Weitere Informationen

- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
