---
title: Debuggen von R-Code
description: Visual Studio stellt eine umfassende Debugoberfläche für R bereit, einschließlich Haltepunkten, Anfügen, Aufrufliste und Variablenprüfung.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: e3696cac00c726cffb76f29a1da2c503a15af2bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885819"
---
# <a name="debug-r-in-visual-studio"></a>Debuggen von R in Visual Studio

Der Integration des vollständigen Debug-Vorgangs von Visual Studio ist in R-Tools für Visual Studio (RTVS) vorhanden (siehe [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md). Diese Unterstützung umfasst Haltepunkte, Anfügen an laufende Prozesse, das Überprüfen und Beobachten von Variablen, sowie das Überprüfen der Aufrufliste. Dieser Artikel erforscht die Aspekte des Debuggens, die in R und RTVS exklusiv sind.

Das Starten des Debuggers für die R-Startdatei in einem R-Projekt funktioniert genauso wie in anderen Projekttypen: Verwenden Sie **Debuggen** > **Debugging starten**, die **F5**-Taste oder die **Startdatei der Quelle** auf der Debugsymbolleiste:

![Debugger-Schaltfläche „Start“ für R](media/debugger-start-button.png)

Um die Startdatei zu ändern, führen Sie einen Rechtsklick auf eine Datei im Projektmappen-Explorer durch, und wählen Sie **Als R-Startskript festlegen** aus.

In jedem Fall führt das Starten des Debuggers dazu, dass die Datei im interaktiven Fenster „eingebunden“ wird, was bedeutet, dass sie dort geladen und ausgeführt wird, wie in der interaktiven Ausgabe von Windows dargestellt wird:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Beachten Sie, dass die `rtvs::debug_source`-Funktion verwendet wird, um das Skript einzubinden. Diese Funktion ist erforderlich, da RTVS Ihren Code als Vorbereitung für das Debuggen bearbeiten muss. Wenn Sie einen Einbindungs-RTVS-Befehl verwenden, und ein Debugger angefügt ist, verwendet Visual Studio automatisch `rtvs::debug_source`.

Sie können den Debugger auch manuell direkt aus dem interaktiven Fenster anfügen mithilfe des Befehls **R-Tools** > **Sitzung** > **Debugger anfügen**, des Befehls **Debuggen** > **An R Interactive anfügen** oder des Befehls **Debugger anfügen** auf der interaktiven Symbolleiste des Fensters. Sobald dies erfolgt ist, müssen Sie die Dateien einbinden, die Sie debuggen möchten. Wenn Sie die Dateien manuell einfügen wollen, stellen Sie sicher, dass Sie `rtvs::debug_source` verwenden und nicht die regulären `source`-Befehl in R.

Diese Verbindung zwischen dem Debugger und dem interaktiven Fenster vereinfacht viele Dinge, z.B. das Aufrufen (und Debuggen) einer Funktion mit unterschiedlichen Parameterwerten. Nehmen wir beispielsweise an, Sie hätten die folgende Funktion in einer eingebundenen Datei (das bedeutet, dass sie in die Sitzung geladen wurde):

```R
add <- function(x, y) {
    return(x + y)
}
```

Dann legen Sie einen Haltepunkt auf der `return`-Anweisung fest. Jetzt hält die Eingabe von `add(4,5)` im interaktiven Fenster den Debugger an Ihrem Haltepunkt an.

## <a name="environment-browser-in-the-interactive-window"></a>Umgebungsbrowser im interaktiven Fenster

Wenn Sie im Debugger angehalten werden, werden Sie auch bei der Aufforderung des Umgebungsbrowsers im [interaktiven Fenster](interactive-repl-for-r-in-visual-studio.md) angehalten. Diese Aufforderung erscheint als `Browse[n]>`, wobei „n“ eine Zahl darstellt.

Der Umgebungsbrowser unterstützt eine Reihe bestimmter Befehle:

| Befehl | Beschreibung |
| --- | --- |
| n | next: führt die nächste Anweisung in der Codedatei aus (das gleiche wie „step over“) |
| s | step into: führt die nächste Anweisung in der Codedatei aus, wobei schrittweise ein Funktionsbereich ausgeführt wird, wenn die nächste Anweisung ein Funktionsaufruf ist. |
| f | finish: führt den Rest des aktuellen Funktionsbereichs aus und wird an den Aufrufer zurückgegeben (genauso wie bei „step out“). |
| c, cont | continue: führt das Programm bis zum nächsten Haltepunkt aus. |
| Q | quits: beendet die Debugsitzung. |
| wo | show stack: zeigt die Aufrufliste im interaktiven Fenster an. |
| help | show help: zeigt verfügbare Befehle im interaktiven Fenster an. |
| &lt;expr&gt; | evaluiert den Ausdruck in *expr*. |

![Umgebungsbrowser im interaktiven Fenster](media/debugger-environment-browser.png)
