---
title: Interaktive REPL für R
description: Verwenden der interaktiven REPL-Umgebung für R in Visual Studio, die in die Editor-Fenster integriert ist.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0355f1017bb661b4f72325fb74f60653f69cd182
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878175"
---
# <a name="work-with-the-r-interactive-window"></a>Arbeiten mit dem R Interactive-Fenster

R Tools für Visual Studio (RTVS) stellt ein interaktives R-Fenster bereit, das auch als **REPL**-Fenster (Read-Evaluate-Print-Loop, „Lesen-Auswerten-Ausgeben“-Schleife) bekannt ist, in das Sie R-Code eingeben und sofort die Ergebnisse sehen können. Alle Module, Syntax und Variablen sowie IntelliSense sind im interaktiven Fenster verfügbar.

Das interaktive Fenster ist auch in den regulären Editorfenstern von R enthalten. Wenn Sie Code auswählen und **STRG**+**Eingabe** drücken oder einen Rechtsklick machen und **Interaktiv ausführen** auswählen, wird der Code Zeile für Zeile im interaktiven Fenster ausgeführt, als würden Sie diesen direkt eingeben. Wenn sich der Cursor in einer einzelnen Zeile in einem Editorfenster befindet, wird durch **STRG**+**Eingabe** diese Zeile an das interaktive Fenster gesendet und der Cursor anschließend in die nächste Zeile bewegt. Auf diese Weise können Sie einfach mehrfach **STRG**+**Eingabe** drücken, um sich schrittweise durch den Code zu bewegen.

Wenn Sie sich mit diesen Features vertraut machen möchten, befolgen Sie die exemplarische Vorgehensweise [Erste Schritte mit R](getting-started-with-r.md) sowie die Anweisungen in den Abschnitten in diesem Artikel. [Codeausschnitte](code-snippets-for-r.md) funktionieren auch im interaktiven Fenster wie in R-Editorfenstern.

## <a name="overview-of-the-interactive-window"></a>Übersicht über das R Interactive-Fenster

Durch die Eingabe von gültigem R-Code und das Drücken der **Eingabetaste** am Ende der Zeile wird der Code in dieser Zeile ausgeführt:

```repl
> 3 + 3
[1] 6
```

Wenn sie die **Eingabetaste** an einer beliebigen Stelle in einer Zeile drücken, führt die Eingabe auch diese Zeile aus.

Die vorherige Eingabe und Ausgabe im REPL ist schreibgeschützt und kann nicht geändert werden. Jedoch können Sie jederzeit Text aus dem Fenster auswählen und kopieren sowie einfügen. Eingefügter Code wird so ausgeführt, als würde er Zeile für Zeile eingefügt werden.

Das heißt, wenn Sie beginnen, eine Anweisung einzugeben und die **Eingabetaste** drücken, weiß RTVS, wann die Anweisung fortgesetzt werden muss und gibt links mit dem passenden Einzug den Mehrzeilenmodus mit der a+-Aufforderung ein. RTVS schließt auch runde Klammern, eckige Klammern und geschweifte Klammern:

![Mehrzeiliger Anweisungseintrag im interaktiven Fenster](media/repl-multiline-entry.png)

In diesem Mehrzeilenmodus wird der Codeblock nur dann über die **Eingabetaste** ausgeführt, wenn dieser am Ende des Blocks positioniert wird. Andernfalls wird eine neue Zeile eingefügt. Sie können jedoch **STRG**+**Eingabetaste** an jeder beliebigen Position drücken, um diesen Codeblock sofort auszuführen.

### <a name="toolbar-commands"></a>Symbolleistenbefehle

Hier sehen Sie das interaktive Fenster mit seiner Symbolleiste:

![Interaktives Fenster mit Symbolleiste](media/repl-window.png)

Die meisten Symbolleistenbefehle, die unten aufgeführt sind, haben Tastaturentsprechungen und sind auch in den Menüs **R Tools** > **Sitzung** und **R Tools** > **Arbeitsverzeichnis** (oder wie aufgeführt) verfügbar:

| Schaltfläche | Befehl | Tastenkombination | Beschreibung |
| --- | --- | --- | --- |
| ![Schaltfläche „Zurücksetzen“](media/repl-toolbar-01-reset.png) | Reset | **STRG**+**UMSCHALT**+**F10** | Setzt die Sitzung des interaktiven Fensters zurück und löscht alle Variablen sowie die Versionsgeschichte. |
| ![Schaltfläche „Löschen“](media/repl-toolbar-02-clear.png) | Clear | **STRG**+**L** | Löscht die Ausgabe, die im interaktiven Fenster angezeigt wird. Beeinträchtigt keine Sitzungsvariablen oder die Versionsgeschichte. |
| ![Schaltflächen zur Versionsgeschichte](media/repl-toolbar-03-history.png) | Vorheriger History-Befehl<br/>Nächster History-Befehl | **Nach oben**, **Nach unten**<br/>**Alt**+**Nach oben**, **Alt**+**Nach unten** | Führt einen Bildlauf durch die Versionsgeschichte mit bestimmten Verhalten für mehrzeilige Codeblöcke aus. Weitere Informationen finden Sie unter [Versionsgeschichte](#history). |
| ![Schaltfläche „Arbeitsbereich laden“](media/repl-toolbar-04-load-workspace.png) | Arbeitsbereich laden | n/v | Lädt einen zuvor gespeicherten Arbeitsbereich (siehe [Arbeitsbereiche und Sitzungen](#workspaces-and-sessions)). |
| ![Schaltfläche „Arbeitsbereich speichern unter“](media/repl-toolbar-05-save-workspace-as.png)| Arbeitsbereich speichern unter | n/v | Speichert den aktuellen Zustand der Sitzung als Arbeitsbereich (siehe [Arbeitsbereiche und Sitzungen](#workspaces-and-sessions)). |
| ![Schaltfläche „R-Skript einbinden“](media/repl-toolbar-06-source-r-script.png) | R-Skript einbinden | **STRG**+**UMSCHALT**+**S** | Ruft `source` mit dem derzeit aktiven R-Skript im Visual Studio-Editor, das den Code ausführt.  Diese Schaltfläche wird nur angezeigt, wenn eine R-Datei im Visual Studio-Editor geöffnet ist. |
| ![Schaltfläche „R-Skript mit Echo einbinden“](media/repl-toolbar-07-source-r-script-with-echo.png) | R-Skript mit Echo einbinden | **STRG**+**UMSCHALT**+**Eingabetaste** | Das gleiche wie „R-Skript einbinden“, es wird jedoch der Inhalt des Skripts im interaktiven Fenster angezeigt. |
| ![Schaltfläche „Interrupt-R“](media/repl-toolbar-08-interrupt-r.png)| Interrupt-R | **ESC** | Hält den ausgeführten Code im interaktiven Fenster an, so wie die `while`-Schleife, die im Screenshot am Anfang dieses Abschnitts dargestellt wird. |
| ![Schaltfläche „Debugger anfügen“](media/repl-toolbar-09b-attach-debugger.png)| Debugger anfügen | n/v | Auch mithilfe des Befehls **Debuggen** > **An R Interactive anfügen** verfügbar. |
| ![Schaltfläche „Arbeitsverzeichnis auf Quelldateispeicherort festlegen“](media/repl-toolbar-10-set-working-directory-source.png)| Arbeitsverzeichnis auf Quelldateispeicherort festlegen | **STRG**+**UMSCHALT**+**E** | Legt das Arbeitsverzeichnis auf die zuletzt eingebundene Datei fest, die in das interaktive Fenster geladen wurde (mithilfe von `source`). Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |
| ![Schaltfläche „Arbeitsverzeichnis auf Projektspeicherort festlegen“](media/repl-toolbar-11-set-working-directory-to-project.png) | Arbeitsverzeichnis auf Projektspeicherort festlegen | **STRG**+**UMSCHALTTASTE**+**P** | Legt das Arbeitsverzeichnis auf den Stamm des zuletzt geladenen Projekts in Visual Studio fest. Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |
| (Textfeld) | Arbeitsverzeichnis auswählen | n/v | Direktes Eingabefeld für das Arbeitsverzeichnis. Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |

## <a name="workspaces-and-sessions"></a>Arbeitsbereiche und Sitzungen

Das Ausführen von Code im interaktiven Fenster erstellt einen Kontext in Ihrer aktuellen Sitzung. Der Kontext besteht aus globalen Variablen, Funktionsdefinitionen, geladenen Bibliotheken usw. Dieser Kontext wird im Allgemeinen als *Arbeitsbereich* bezeichnen. Sie können Arbeitsbereiche jederzeit speichern und laden.

Wenn Sie die Schaltfläche **Arbeitsbereich speichern unter** auswählen oder den Befehl **R Tools** > **Sitzung** > **Arbeitsbereich speichern unter** verwenden, werden Sie zur Eingabe eines Speicherorts und eines Dateinamens aufgefordert (die Standarderweiterung lautet *RDATA*).

Wenn sie einen Arbeitsbereich mit einem bestimmten Dateinamen speichern möchten (standardmäßig *RDATA*), klicken sie auf die Schaltfläche **Arbeitsbereich speichern** in der REPL:

Wenn Sie einen kürzlich gespeicherten Arbeitsbereich erneut laden möchten, wählen Sie die Schaltfläche **Arbeitsbereich laden** aus, oder verwenden Sie **R Tools** > **Sitzung** > **Arbeitsbereich laden**, und navigieren Sie zu der Arbeitsbereichdatei.

Über die Schaltfläche **Zurücksetzen** oder **R Tools** > **Sitzung** > **Zurücksetzen** können Sie den Sitzungskontext löschen. Wenn Sie eine Remotesitzung verwenden, wird beim Zurücksetzen auch das Benutzerprofil auf dem Remotecomputer gelöscht, damit alle darin gespeicherten Dateien gelöscht werden. (Siehe [Arbeitsbereiche](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Arbeitsverzeichnis

Entwickler möchten häufig ihr Arbeitsverzeichnis ändern, während sie sich in einer interaktiven Sitzung befinden. Mithilfe verschiedener Befehle, die auf der Symbolleiste zur Verfügung stehen, sowie über das Menü **R Tools** > **Arbeitsverzeichnis** und das Kontextmenü des Projekts können Sie ohne großen Aufwand ein Arbeitsverzeichnis am Speicherort einer Quelldatei, am Speicherort Ihres Projekts oder an jedem anderen beliebigen Speicherort erstellen. Damit müssen Sie nicht länger vollständige Pfadnamen oder lange relative Pfadnamen eingeben, wenn Sie sich auf Dateien beziehen.

## <a name="history"></a>Versionsgeschichte

Jede Zeile, die Sie im interaktiven Fenster eingeben, enthält von einem Editor gesendete Zeilen, die in der REPL-Versionsgeschichte gespeichert sind. Sie können mit den NACH-OBEN- und NACH-UNTEN-TASTEN durch die Versionsgeschichte navigieren, wie sie es wahrscheinlich von der Befehlszeile kennen.

Ein Unterschied ist, dass, wenn Sie beginnen, etwas in der aktuellen Zeile einzugeben und dann auf die NACH-OBEN-TASTE drücken, die aktuelle Zeile in Ihrer Versionsgeschichte gespeichert wird, auch wenn Sie diese Zeile noch nicht ausgeführt haben.

Die Versionsgeschichte im interaktiven Fenster arbeitet intelligent mit den Anweisungen eines anderen mehrzeiligen Codeblocks zusammen. Wenn Sie mithilfe der NACH-OBEN- und NACH-UNTEN-TASTEN durch die Versionsgeschichte browsen, werden mehrzeilige Codeblöcke als ganze Einheit abgerufen und als aktueller Eintrag dargestellt. Zu diesem Zeitpunkt navigieren die Pfeiltasten Zeile für Zeile durch den Codeblock, bis das obere oder untere Ende erreicht ist. Am oberen Rand des Codeblocks ruft die NACH-OBEN-TASTE das vorherige Element in der Versionsgeschichte ab. Am unteren Rand ruft die NACH-UNTEN-TASTE das nächste Element ab.

Durch dieses Verhalten erfolgt eine Anpassung, wenn das letzte Element in der Versionsgeschichte mit der Tastenkombination NACH-OBEN-TASTE und **Eingabetaste** erneut ausgeführt wird, wobei die Bearbeitung eines mehrzeiligen Codeblocks durch Drücken der NACH-OBEN-TASTE natürlich zugelassen wird, damit Sie darin navigieren können.

Verwenden Sie zur Vermeidung einer Navigation in mehrzeiligen Codeblöcken die Schaltflächen der Symbolleiste oder **Alt**+**Nach oben** und **Alt**-**Nach unten**, damit alle Blöcke als einzelne Zeilen behandelt werden.

Der einfachste Weg zum Kennenlernen der Verlaufsfeatures ist, diese selbst im interaktiven Fenster zu testen. Der unten dargestellte Code stellt einige passende einzeilige und mehrzeilige Anweisungen dar. Kopieren Sie jede Anweisung und fügen Sie sie einzeln ein, um die passende Versionsgeschichte zu erstellen. (Sie können den Code auch in eine separate Codedatei einfügen und die Zeilen durch Drücken von **STRG**+**Eingabetaste** an das interaktive Fenster senden.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```