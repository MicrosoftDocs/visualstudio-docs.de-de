---
title: Analysieren der Speicherauslastung
ms.custom: seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0262081489ec6e037a006649c3041baf02b32d58
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007220"
---
# <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung

Zum Ermitteln von Arbeitsspeicherverlusten und ineffizienter Arbeitsspeichernutzung können Sie Tools wie das im Debugger integrierte Speicherauslastungs-Diagnosetool oder die Tools im Leistungs-Profiler verwenden, z. B. das .NET-Objektzuordnungstool und das Speicherauslastungs-Nachbereitungstool.

Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und systemeigenen Momentaufnahme-Heaps machen. Sie können Momentaufnahmen von .NET-Apps, ASP.NET-Apps, C++-Apps und Apps im gemischten Modus (.NET und nativ) erfassen. Das **Speicherauslastungstool** kann für ein geöffnetes Visual Studio-Projekt oder eine installierte Microsoft Store-App ausgeführt oder an eine ausgeführte App bzw. einen Prozess angefügt werden. Sie können das **Speicherauslastungstool** mit oder ohne Debuggen ausführen. Weitere Informationen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Im Debugger können Sie die Arbeitsspeicher-Profilerstellung aktivieren bzw. deaktivieren und eine objektspezifische Aufschlüsselung der Arbeitsspeicherauslastung anzeigen. Sie können die Ergebnisse der Arbeitsspeicherauslastung anzeigen, wenn die Ausführung pausiert ist, z. B. an einem Breakpoint.

.NET-Entwickler können zwischen dem Tool für [Arbeitsspeicherauslastung](../profiling/memory-usage.md) und dem [.NET-Tool für Objektzuordnungen](../profiling/dotnet-alloc-tool.md) auswählen.
- Das Tool für **.NET-Objektzuordnungen** unterstützt Sie dabei, Zuteilungsmuster und Anomalien in Ihrem .NET-Code zu entdecken, und es unterstützt Sie beim Identifizieren häufiger Probleme mit der Garbage Collection. Dieses Tool wird nur zur Nachbereitung ausgeführt. Sie können dieses Tool auf lokalen Computern oder Remotecomputern ausführen.
- Das Tool für **Arbeitsspeicherauslastung** ist hilfreich für das Identifizieren von Arbeitsspeicherverlusten, die bei .NET-Apps nicht allzu häufig auftreten. Wenn Sie Debuggerfeatures für das Überprüfen des Arbeitsspeichers verwenden müssen, z. B. für das schrittweise Ausführen von Code, wird das [im Debugger integrierte Tool für die Arbeitsspeicherauslastung](../profiling/beginners-guide-to-performance-profiling.md) empfohlen.

Unter Windows 7 und höher können Sie die Profilerstellungstools ohne den Debugger verwenden. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools** ).

## <a name="blogs-and-videos"></a>Blogs und Videos

[Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Team Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Teamblog: Speicherprofilerstellung in Visual C++ 2015)](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Siehe auch

- [Analysieren der Speicherauslastung ohne den Debugger](../profiling/memory-usage-without-debugging2.md)
- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
