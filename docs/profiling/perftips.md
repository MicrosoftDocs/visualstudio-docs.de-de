---
title: PerfTips | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7003f75b59773e8761095c15826bf5e6abcf23ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331053"
---
# <a name="perftips"></a>PerfTips
Visual Studio-Debugger *PerfTips* und die in den Debugger integrierten **Diagnosetools** helfen Ihnen beim Überwachen und Analysieren der Leistung Ihrer App während des Debuggens.

 Obgleich die Debugger-integrierten Diagnosetools eine hervorragende Möglichkeit sind, über Leistungsprobleme während der Entwicklung in Kenntnis gesetzt zu werden, kann der Debugger die Leistung Ihrer App erheblich beeinträchtigen. Zum Erfassen genauerer Leistungsdaten sollten Sie die Visual Studio-Diagnosetools, die auch außerhalb des Debuggers ausgeführt werden können, als zusätzliche Komponente bei Ihren Leistungsuntersuchungen in Erwägung ziehen. Weitere Informationen finden Sie unter [Profilerstellungstools mit oder ohne den Debugger ausführen](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>PerfTips
 Wenn der Debugger die Ausführung an einem Haltepunkt oder während einer schrittweisen Ausführung stoppt, wird die verstrichene Zeit zwischen der Pause und dem vorherigen Haltepunkt als QuickInfo im Editor-Fenster angezeigt. Weitere Informationen finden Sie unter [PerfTips: Leistungsinformationen auf einen Blick beim Debuggen mit Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Fenster "Diagnosetools"
 Breakpoints und die zugehörigen Zeitsteuerungsdaten werden im Fenster **Diagnosetools** aufgezeichnet.

 Folgende Abbildung zeigt das Fenster **Diagnosetools** in Visual Studio 2015 Update 1:

 ![Diagnosetools-Update1](../profiling/media/diagnostictools-update1.png "Diagnosetools-Update1")

- Die **Haltepunkt** -Zeitachse kennzeichnet die Haltepunkte, die während der Debugsitzung ermittelt wurden. Klicken Sie auf ein Ereignis, um die **Debugger** -Detailliste auszuwählen.

- Das Diagramm **CPU-Auslastung** zeigt die Änderung in der CPU übergreifend über alle Prozessorkerne in der Debugsitzung an.

- Die Liste **Ereignisse** des **Debugger** -Detailbereichs enthält Elemente für jeden Haltepunkt.

- Die Spalte **Dauer** eines Haltepunkt-Ereignisses zeigt die verstrichene Zeit zwischen Ereignis und dem vorherigen Haltepunkt an.

## <a name="turn-perftips-on-or-off"></a>Aktivieren oder Deaktivieren von PerfTips
 So aktivieren oder deaktivieren Sie PerfTips:

1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen**aus.

2. Markieren Sie **PerfTip für verstrichene Zeit beim Debuggen anzeigen**oder heben Sie die Auswahl auf.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Aktivieren oder deaktivieren Sie das Fenster „Diagnosetools“
 Zum Aktivieren oder deaktivieren das Fenster „Diagnosetools“:

1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen**aus.

2. Aktivieren oder deaktivieren Sie **Aktivieren der Diagnosetools während des Debuggens**.

## <a name="see-also"></a>Siehe auch
- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
