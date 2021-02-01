---
title: Optimieren der Profilereinstellungen | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zum Leistungs-Profiler und zum Fenster „Diagnosetools“ in Visual Studio. Diese umfassen viele verschiedene Einstellungen, die sich auf die Gesamtleistung der Tools auswirken.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 482ee640f4b84348e00f2f3da42a4dbe13f73460
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722840"
---
# <a name="optimizing-profiler-settings"></a>Optimieren der Profilereinstellungen

Der Leistungs-Profiler und das Fenster „Diagnosetools“ in Visual Studio umfassen viele verschiedene Einstellungen, die sich auf die Gesamtleistung der Tools auswirken. Durch das Ändern einiger Einstellungen kann die Analyse schneller ausgeführt werden, oder es können längere Wartezeiten beim Verarbeiten von Ergebnissen in den Tools entstehen. Nachfolgend finden Sie eine Übersicht bestimmter Einstellungen und ihrer Auswirkungen auf die Leistung.

## <a name="symbol-settings"></a>Symboleinstellungen

Die Symboleinstellungen in den Debuggeroptionen (**Debuggen > Optionen > Symbole** oder **Extras > Optionen > Debuggen > Symbole**) haben erheblichen Einfluss darauf, wie lang es dauert, Ergebnisse in den Tools zu generieren. Die Aktivierung von Symbolservern oder die Verwendung von **_NT_SYMBOL_PATH** führt dazu, dass der Profiler Symbole für jedes Modul anfordert, das in einem Bericht geladen wurde. Aktuell lädt der Profiler automatisch alle Symbole, unabhängig von der Einstellung zum automatischen Laden von Symbolen.

![Seite zum Laden von Symbolen](../profiling/media/symbolloading.png "Seite zum Laden von Symbolen")

Der Fortschritt beim Laden von Symbolen kann im Fenster **Ausgabe** unter der Überschrift **Diagnosetools** angezeigt werden.

![Fortschritt beim Laden von Symbolen](../profiling/media/symbolloadingprogress.png "Fortschritt beim Laden von Symbolen")

Nach dem Download werden die Symbole zwischengespeichert, wodurch zukünftige Analysen beschleunigt werden. Die Dateien müssen aber weiterhin geladen und analysiert werden. Wenn das Laden von Symbolen die Analyse verlangsamt, deaktivieren Sie die Symbolserver, und löschen Sie Ihren Symbolcache. Verwenden Sie stattdessen lokal erstellte Symbole für Ihr Projekt.

## <a name="show-external-code"></a>Externen Code anzeigen

Viele der Tools im **Leistungs-Profiler** und im Fenster **Diagnosetools** unterscheiden zwischen Benutzercode und externem Code. Benutzercode ist jeglicher Code, der über die geöffnete Projektmappe oder einen geöffneten Arbeitsbereich erstellt wird. Externer Code ist alles andere. Wenn Sie die Einstellung **Externen Code anzeigen** deaktiviert lassen oder **Nur meinen Code anzeigen** aktivieren, ermöglichen Sie es den Tools, externen Code in einem einzigen Frame oberster Ebene zu aggregieren, wodurch der Verarbeitungsaufwand zur Anzeige der Ergebnisse erheblich gesenkt wird. Auf diese Weise können Benutzer sehen, welche Aufrufe in externem Code zu einer Verlangsamung geführt haben, während die zu verarbeitenden Daten auf ein Minimum beschränkt werden. Sofern möglich, lassen Sie die Option **Externen Code anzeigen** deaktiviert, und stellen Sie sicher, dass Sie die Projektmappe oder den Arbeitsbereich für die Diagnosesitzung geöffnet haben, die bzw. den Sie analysieren möchten.

## <a name="trace-duration"></a>Dauer der Ablaufverfolgung

Eine Profilerstellung mit geringerer Dauer führt zu weniger Daten, die schneller analysiert werden können. Normalerweise wird empfohlen, bei der Ablaufverfolgung nicht länger als 5 Minuten Leistungsdaten zu erfassen. Einige Tools, z. B. das Tool [CPU-Nutzung](../profiling/cpu-usage.md), ermöglichen Ihnen das Aussetzen der Datensammlung während der Toolausführung, sodass Sie die Datenmenge einschränken können, die für das zu analysierend Szenario erfasst werden.

## <a name="sampling-frequency"></a>Stichprobenhäufigkeit

Bestimmte Tools, z. B. das Tool [GPU-Nutzung](../profiling/cpu-usage.md) und das Tool [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md) erlauben eine Anpassung der Stichprobenhäufigkeit. Durch das Erhöhen der Stichprobenhäufigkeit wird eine genauere Messung durchgeführt, aber gleichzeitig erhöht sich die generierte Datenmenge. Normalerweise ist es am besten, für diese Einstellung die Standardhäufigkeit beizubehalten, sofern nicht ein bestimmtes Problem untersucht werden soll.

![Eigenschaftenseite im Diagnosehub](../profiling/media/diaghubpropertiespage.png "Eigenschaftenseite im Diagnosehub")

## <a name="see-also"></a>Siehe auch

- [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Gleichzeitiges Verwenden mehrerer Profilertools](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Grundlegendes zu Leistungsauflistungsmethoden](../profiling/understanding-performance-collection-methods-perf-profiler.md)
