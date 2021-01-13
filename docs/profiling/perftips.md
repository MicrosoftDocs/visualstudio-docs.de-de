---
title: PerfTips | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie PerfTips des Visual Studio-Debuggers sowie integrierte Diagnosetools verwenden können, um die Leistung Ihrer App während des Debuggens zu überwachen und zu analysieren.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 481113e9f5e2f5b66aec5f4dad29f581462165ca
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815827"
---
# <a name="perftips"></a>PerfTips

Visual Studio-Debugger *PerfTips* und die in den Debugger integrierten **Diagnosetools** helfen Ihnen beim Überwachen und Analysieren der Leistung Ihrer App während des Debuggens.

Obgleich die Debugger-integrierten Diagnosetools eine hervorragende Möglichkeit sind, über Leistungsprobleme während der Entwicklung in Kenntnis gesetzt zu werden, kann der Debugger die Leistung Ihrer App erheblich beeinträchtigen. Zum Erfassen genauerer Leistungsdaten sollten Sie die Tools im Leistungs-Profiler als zusätzliche Komponente bei Ihren Leistungsuntersuchungen in Erwägung ziehen. Weitere Informationen finden Sie unter [Profilerstellungstools mit oder ohne den Debugger ausführen](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>PerfTips

Wenn der Debugger die Ausführung an einem Haltepunkt oder während einer schrittweisen Ausführung stoppt, wird die verstrichene Zeit zwischen der Pause und dem vorherigen Haltepunkt als QuickInfo im Editor-Fenster angezeigt. Weitere Informationen finden Sie unter [PerfTips: Leistungsinformationen auf einen Blick beim Debuggen mit Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Fenster "Diagnosetools"

Breakpoints und die zugehörigen Zeitsteuerungsdaten werden im Fenster **Diagnosetools** aufgezeichnet.

In der folgenden Abbildung ist das Fenster **Diagnosetools** dargestellt.

![Screenshot des Fensters „Diagnosetools“ im Visual Studio-Debugger mit der Zeitachse für Ereignisse und Diagrammen für Arbeitsspeicher- und CPU-Auslastung.](../profiling/media/diagnostictools-update1.png)

- Die **Haltepunkt** -Zeitachse kennzeichnet die Haltepunkte, die während der Debugsitzung ermittelt wurden. Klicken Sie auf ein Ereignis, um die **Debugger** -Detailliste auszuwählen.

- Das Diagramm **CPU-Auslastung** zeigt die Änderung in der CPU übergreifend über alle Prozessorkerne in der Debugsitzung an.

- Die Liste **Ereignisse** des **Debugger** -Detailbereichs enthält Elemente für jeden Haltepunkt.

- Die Spalte **Dauer** eines Haltepunkt-Ereignisses zeigt die verstrichene Zeit zwischen Ereignis und dem vorherigen Haltepunkt an.

## <a name="turn-perftips-on-or-off"></a>Aktivieren oder Deaktivieren von PerfTips

So aktivieren oder deaktivieren Sie PerfTips:

1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen** aus.

2. Markieren Sie **PerfTip für verstrichene Zeit beim Debuggen anzeigen** oder heben Sie die Auswahl auf.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Aktivieren oder deaktivieren Sie das Fenster „Diagnosetools“

Zum Aktivieren oder deaktivieren das Fenster „Diagnosetools“:

1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen** aus.

2. Aktivieren oder deaktivieren Sie **Aktivieren der Diagnosetools während des Debuggens**.

## <a name="see-also"></a>Siehe auch

- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
