---
title: Häufige Muster von Multithread-Apps mit unerwünschtem Verhalten
description: Erfahren Sie mehr über die gängigen Muster von Multithreadanwendungen mit unerwünschtem Verhalten, die in der Visual Studio-Parallelitätsschnellansicht enthalten sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36e14640da4d66134ca961607f66f6a355f6b9d9
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815788"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Häufige Muster von Multithreadanwendungen mit unerwünschtem Verhalten

Die Parallelitätsschnellansicht ermöglicht Entwicklern die visuelle Darstellung des Verhaltens einer Multithreadanwendung. Dieses Tool enthält einen Katalog mit häufigen Mustern von Multithreadanwendungen mit unerwünschtem Verhalten. Der Katalog umfasst typische und erkennbare visuelle Muster, die durch das Tool sichtbar gemacht werden. Außerdem wird das Verhalten erläutert, das durch das jeweilige Muster dargestellt wird, und das wahrscheinliche Ergebnis des Verhaltens und der gängigste Ansatz zu seiner Lösung werden aufgezeigt.

## <a name="lock-contention-and-serialized-execution"></a>Sperrkonflikte und serialisierte Ausführung

![Sperrkonflikt, der zu serialisierter Ausführung führt](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Eine parallelisierte Anwendung wird manchmal weiter seriell ausgeführt, obwohl mehrere Threads vorhanden sind und der Computer über eine ausreichende Anzahl von logischen Kernen verfügt. Das erste Symptom ist eine schlechte Multithreadleistung – unter Umständen sogar noch etwas schlechter als bei der seriellen Implementierung. In der Threadansicht werden keine parallel ausgeführten Threads angezeigt. Stattdessen sehen Sie, dass immer nur ein einzelner Thread ausgeführt wird. Wenn Sie an diesem Punkt in einem Thread auf ein Synchronisierungssegment klicken, werden eine Aufrufliste für den blockierten Thread (Aufrufliste für Blockierungen) sowie der Thread angezeigt, von dem die Blockierbedingung entfernt wurde (Aufrufliste für Blockierungsaufhebungen). Wenn die Aufrufliste für die Blockierungsaufhebung Teil des zu analysierenden Prozesses ist, wird auch ein threadkompatibler Konnektor angezeigt. Von hier können Sie zum Code der Aufruflisten für die Blockierung und für die Blockierungsaufhebung navigieren, um die Ursache der Serialisierung genauer zu untersuchen.

Wie in der folgenden Abbildung gezeigt, kann die Parallelitätsschnellansicht dieses Symptom auch in der CPU-Auslastungsansicht anzeigen, wo die Anwendung trotz mehrerer Threads nur einen logischen Kern nutzt.

Weitere Informationen finden Sie im Abschnitt „Start with the problem (Beim Problem beginnen)“ im MSDN Magazine-Artikel [Thread Performance – Resource Contention Concurrency Profiling in Visual Studio 2010 (Threadleistung – Parallelitätsprofilerstellung für Ressourcenkonflikte in Visual Studio 2010)](/archive/msdn-magazine/2010/june/msdn-magazine-thread-performance-resource-contention-concurrency-profiling-in-visual-studio-2010).

![Sperrkonflikt](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Ungleiche Arbeitslastverteilung

![Screenshot eines Workloaddiagramms für parallele Threads in der Parallelitätsschnellansicht. Die Threads enden zu unterschiedlichen Zeiten, und weisen deshalb ein Treppenstufenmuster auf.](../profiling/media/unevenworkload_1.png)

Bei einer unregelmäßigen Verteilung der Arbeitslast auf mehrere parallele Threads in einer Anwendung tritt nach Abschluss der Ausführung der Threads ein typisches Treppenmuster auf. Dieses wird in der obigen Abbildung gezeigt. Die Parallelitätsschnellansicht zeigt in der Regel sehr nahe beieinander liegende Startzeiten für die einzelnen parallelen Threads an. Normalerweise werden diese Threads jedoch nicht gleichzeitig, sondern unregelmäßig beendet. Dieses Muster deutet auf eine unregelmäßige Verteilung der Arbeitslast in einer Gruppe paralleler Threads hin, was sich negativ auf die Leistung auswirken kann. Die beste Methode, dieses Problem zu beheben, besteht darin, den Algorithmus erneut auszuwerten, mit dem die Arbeitslast auf die parallelen Threads aufgeteilt wurde.

Wie in der folgenden Abbildung gezeigt wird, kann dieses Symptom von der Parallelitätsschnellansicht auch als graduelle Abstufung der CPU-Nutzung in der CPU-Auslastungsansicht dargestellt werden.

![Screenshot der CPU-Nutzungsansicht in der Parallelitätsschnellansicht mit einem Treppenstufenmuster am Ende des CPU-Auslastungsdiagramms.](../profiling/media/unevenworkload_2.png)

## <a name="oversubscription"></a>Überzeichnung

![Screenshot eines Workloaddiagramms für alle aktiven Threads in der Parallelitätsschnellansicht. Eine Legende zeigt die mit „Ausführung“ und „Vorzeitiger Entfernung“ verbrachte Zeit.](../profiling/media/oversubscription.png)

Im Falle einer Überzeichnung ist die Anzahl der aktiven Threads in einem Prozess größer als die Anzahl der verfügbaren logischen Kerne im System. Die obige Abbildung zeigt die Ergebnisse der Überzeichnung mit erheblicher vorzeitiger Entfernung der Zeilenbildung in allen aktiven Threads. Darüber hinaus zeigt die Legende, dass ein großer Prozentsatz der Zeit auf die vorzeitige Entfernung entfällt (84 Prozent in diesem Beispiel). Dies zeigt möglicherweise an, dass das System vom Prozess aufgefordert wird, mehr parallele Threads auszuführen, als logische Kerne vorhanden sind. Es kann jedoch auch sein, dass Ressourcen von anderen Prozessen im System verwendet werden, die eigentlich für diesen Prozess zur Verfügung stehen sollten.

Beachten Sie beim Auswerten dieses Problems Folgendes:

- Das Gesamtsystem ist möglicherweise überzeichnet. Beachten Sie, dass die Threads möglicherweise von anderen Prozessen im System präemptiv unterbrochen werden. Wenn Sie den Cursor in der Threadansicht über einem Segment mit vorzeitiger Entfernung ruhen lassen, werden der Thread und der Prozess, von dem dieser präemptiv unterbrochen wurde, in einer QuickInfo benannt. Bei diesem Prozess muss es sich nicht zwingend um den Prozess handeln, der während der gesamten präemptiven Unterbrechung des Prozesses ausgeführt wurde, Sie erhalten dadurch jedoch einen Hinweis auf mögliche Ursachen für die präemptive Unterbrechung.

- Untersuchen Sie, wie die entsprechende Anzahl der Threads zur Ausführung in dieser Arbeitsphase vom Prozess ermittelt wird. Wenn der Prozess die Anzahl der aktiven parallelen Threads direkt berechnet, können Sie den Algorithmus ändern, um der Anzahl der verfügbaren logischen Kerne auf dem System besser Rechnung zu tragen. Bei Verwendung von Concurrency Runtime, Task Parallel Library oder PLINQ wird die Anzahl der Threads von diesen Bibliotheken berechnet.

## <a name="inefficient-io"></a>Ineffizienter E/A

![Ineffizienter E/A](../profiling/media/inefficient_io.png "Inefficient_IO")

Die übermäßige oder missbräuchliche E/A-Verwendung ist ein häufiger Grund für Ineffizienz in Anwendungen. Sehen Sie sich die obige Abbildung an. Laut sichtbarem Zeitachsenprofil entfallen 44 Prozent der sichtbaren Threadzeit auf E/A-Vorgänge. Die Zeitachse zeigt umfangreiche E/A an, die angeben, dass die profilierte Anwendung häufig durch E/A blockiert wird. Detaillierte Informationen zu den E/A-Arten und zu Blockierungen im Programm erhalten Sie durch Vergrößern der problematischen Bereiche, Untersuchen des sichtbaren Zeitachsenprofils und Klicken auf einen bestimmten E/A-Block, um aktuelle Aufruflisten anzuzeigen.

## <a name="lock-convoys"></a>Kolonnensperren

![Kolonnensperren](../profiling/media/lock_convoys.png "Lock_Convoys")

Kolonnensperren treten auf, wenn zum Abrufen die First-In-First-Out-Reihenfolge verwendet wird und die Ankunftsrate bei der Sperre höher ist als die Abrufrate. Aufgrund des Zusammentreffens dieser beiden Bedingungen laufen nach und nach Anforderungen der Sperre auf. Eine Möglichkeit, dieses Problem zu beheben, besteht darin, „unfaire“ Sperren oder Sperren zu verwenden, die Zugriff auf den ersten Thread ermöglichen, um den entsprechenden entsperrten Zustand zu finden. Die obige Abbildung zeigt dieses Kolonnenverhalten. Zum Beheben dieses Problems verringern Sie die Konflikte um die Synchronisierungsobjekte, verwenden Sie zudem unfaire Sperren.

## <a name="see-also"></a>Siehe auch

[Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)