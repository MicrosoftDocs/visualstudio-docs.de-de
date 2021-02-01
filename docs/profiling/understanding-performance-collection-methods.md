---
title: Grundlegendes zu Leistungserfassungsmethoden | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu den verschiedenen Szenarios, in denen das Erfassen von Daten mit einer bestimmten Methode erfolgen kann.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3bbbef2c6f7bb2ab02731bfbac0dc60d75a3437
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722333"
---
# <a name="understand-performance-collection-methods"></a>Grundlegendes zu Leistungserfassungsmethoden

Die Visual Studio-Tools zur Profilerstellung bieten fünf Methoden zum Sammeln von Leistungsdaten. In diesem Artikel werden die verschiedenen Methoden beschrieben sowie einige Szenarien behandelt, in denen die Datensammlung mithilfe einer bestimmten Methode erfolgen kann.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Weitere Informationen finden Sie unter [Leistungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Methode|Beschreibung|
|------------|-----------------|
|[Sampling](#sampling)|Dient zum Sammeln statistischer Daten zu den von einer App erledigten Aufgaben.|
|[Instrumentierung](#instrumentation)|Dient zum Sammeln ausführlicher Zeitsteuerungsinformationen zu den einzelnen Funktionsaufrufen.|
|[Parallelität](#concurrency)|Dient zum Sammeln ausführlicher Informationen zu Multithread-Apps.|
|[.NET-Arbeitsspeicher](#net-memory)|Dient zum Sammeln ausführlicher Informationen zur .NET-Speicherbelegung und zur Garbage Collection.|
|[Ebeneninteraktion](#tier-interaction)|Dient zum Sammeln von Informationen zu synchronen, an eine SQL Server-Datenbank gerichteten ADO.NET-Funktionsaufrufen.<br /><br /> Profildaten zur Ebeneninteraktion können mit jeder Visual Studio-Edition erfasst werden. Sie können diese Daten jedoch nur in Visual Studio Enterprise anzeigen.|

Mit einigen Profilerstellungsmethoden können auch weitere Daten gesammelt werden, z. B. Leistungsindikatoren für Software und Hardware. Weitere Informationen finden Sie unter [Sammeln zusätzlicher Leistungsdaten](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Sampling

Bei der Samplingmethode für die Profilerstellung werden statistische Daten zu den Aufgaben gesammelt, die während einer Profilerstellung von einer App ausgeführt wurden. Die Samplingmethode ist schlank und wirkt sich kaum auf die Ausführung von App-Methoden aus.

Sampling ist die Standardmethode der Profilerstellungstools von Visual Studio. Sie kann bei folgenden Aufgaben hilfreich sein:

- Erste Untersuchungen der Leistung Ihrer App
- Untersuchung von Leistungsproblemen, die die Auslastung des Mikroprozessors (CPU) betreffen

Bei der Samplingmethode für die Profilerstellung wird die CPU des Computers in festgelegten Abständen unterbrochen und die Funktionsaufrufliste erfasst. Exklusive Samplinganzahlen werden für die gerade ausgeführte Funktion erhöht. Inklusive Anzahlen werden für alle aufrufenden Funktionen in der Aufrufliste erhöht. Samplingberichte enthalten die Summen dieser Anzahlen für die Module, Funktionen, Quellcodezeilen und Anweisungen, für die das Profil erstellt wurde.

Das Samplingintervall wird vom Profiler standardmäßig auf CPU-Zyklen festgelegt. Sie können den Intervalltyp auf einen anderen CPU-Leistungsindikator oder die Anzahl der Leistungsindikatorereignisse für das Intervall festlegen. Sie können auch Daten zur Erstellung eines Profils der Ebeneninteraktion sammeln. Diese Daten geben Aufschluss über die Abfragen, die über ADO.NET an eine SQL Server-Datenbank gerichtet wurden.

[Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)

[Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentierung

Bei der Instrumentierungsmethode zur Profilerstellung werden ausführliche Zeitsteuerungsinformationen für die Funktionsaufrufe in der App gesammelt, für die das Profil erstellt wird. Die Profilerstellung mithilfe der Instrumentierung ist für diese Aufgaben nützlich:

- Untersuchung von Engpässen bei Eingabe/Ausgabe (beispielsweise Datenträger-E/A)
- Gründliche Untersuchung eines bestimmten Moduls oder einer bestimmten Gruppe von Funktionen

Mit der Instrumentierungsmethode wird Code in eine Binärdatei eingefügt. Der Code erfasst Zeitsteuerungsinformationen für alle Funktionen in der instrumentierten Datei und jeden Funktionsaufruf, den diese Funktionen vornehmen. Die Instrumentierung erkennt auch, wenn eine Funktion das Betriebssystem für Vorgänge wie das Schreiben von Daten in eine Datei aufruft.

Die Gesamtzeit, die für eine Funktion oder für eine Quellcodezeile aufgewendet wurde, wird in den Instrumentierungsberichten mithilfe dieser vier Werte dargestellt:

- Verstrichene inklusive Zeit: die benötigte Gesamtzeit zur Ausführung der Funktion oder Quellcodezeile.

- Inklusive Anwendungszeit: die benötigte Zeit zur Ausführung der Funktion oder Quellcodezeile. An das Betriebssystem gerichtete Aufrufe sind ausgeschlossen.

- Verstrichene exklusive Zeit: die benötigte Zeit zur Ausführung der Funktion oder Quellcodezeile. Aufrufe anderer Funktionen sind ausgeschlossen.

- Exklusive Anwendungszeit: die benötigte Zeit zur Ausführung der Funktion oder Quellcodezeile. An das Betriebssystem oder andere Funktionen gerichtete Aufrufe sind ausgeschlossen.

Mithilfe der Instrumentierungsmethode können auch CPU- sowie Softwareleistungsindikatoren erfasst werden.

[Grundlagen zu Instrumentierungsdatenwerten](../profiling/understanding-instrumentation-data-values.md)

[Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Parallelität

Bei der Parallelitätsprofilerstellung werden Informationen zu Multithread-Apps gesammelt. Bei der Profilerstellung für Ressourcenkonflikte werden immer dann ausführliche Aufruflisteninformationen gesammelt, wenn konkurrierende Threads auf den Zugriff auf eine freigegebene Ressource warten müssen. Bei der Parallelitätsvisualisierung werden zusätzlich allgemeinere Informationen zur Interaktion der Multithread-App mit folgenden Elementen gesammelt:

- Sich selbst
- Der Hardware
- Dem Betriebssystem
- Anderen Prozessen auf dem Hostcomputer

In Berichten zu Ressourcenkonflikten wird die Gesamtanzahl der Konflikte angezeigt. Sie melden außerdem die Gesamtzeit, die Module, Funktionen, Quellcodezeilen und Anweisungen auf eine Ressource gewartet haben. Die aufgetretenen Konflikte werden in Zeitachsendiagrammen dargestellt.

In der Parallelitätsschnellansicht werden grafische Informationen gezeigt, mit deren Hilfe Sie Folgendes finden:

- Leistungsengpässe
- CPU-Unterauslastung
- Threadkonflikte
- Threadmigration
- Synchronisierungsverzögerungen
- Bereiche mit überlappenden E/A-Vorgängen

  Nach Möglichkeit ist die grafische Ausgabe mit Daten aus der Aufrufliste und dem Quellcode verknüpft. Daten zur Parallelitätsvisualisierung können nur für Befehlszeilen- und Windows-Apps gesammelt werden.

[Grundlagen zu Ressourcenkonflikt-Datenwerten](../profiling/understanding-resource-contention-data-values.md)

[Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md)

[Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)

[Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET-Speicher

Die Profilerstellungsmethode für die .NET-Speicherzuteilung unterbricht die CPU bei jeder Zuteilung eines .NET Framework-Objekts in einer App, für die ein Profil erstellt wird. Wenn der Profiler auch Daten zur Lebensdauer von Objekten sammelt, unterbricht er die CPU nach jeder Garbage Collection von .NET Framework.

Vom Profiler werden Informationen zu Typ, Größe und Anzahl der Objekte gesammelt, die bei einer Speicherzuteilung erstellt oder bei einer Garbage Collection zerstört wurden.

- Bei Auftreten eines Speicherbelegungsereignisses werden weitere Informationen zur Funktionsaufrufliste gesammelt. Der Profiler erhöht die Anzahl der exklusiven Zuteilungen für die gerade ausgeführte Funktion. Er erhöht auch die inklusiven Anzahlen für alle aufrufenden Funktionen in der Aufrufliste. .NET-Berichte enthalten die Summen dieser Anzahlen für die Typen, Module, Funktionen, Quellcodezeilen und Anweisungen, für die das Profil erstellt wurde.

- Bei der Garbage Collection werden vom Profiler Daten zu den zerstörten Objekten sowie zu den Objekten in den einzelnen generierten Garbage Collections gesammelt. Am Ende der Profilerstellung werden Daten zu den Objekten erfasst, die nicht explizit zerstört wurden. Der Bericht „Objektlebensdauer“ enthält die Summen für jeden Typ, der im Rahmen der Profilerstellung zugeteilt wurde.

Die .NET-Speicherprofilerstellung kann sowohl im Sampling- als auch im Instrumentierungsmodus verwendet werden. Der gewählte Modus besitzt keine Auswirkungen auf die Berichte zur Zuteilung oder Objektlebensdauer, die für die .NET-Speicherprofilerstellung spezifisch sind.

- Wenn Sie die Erstellung von .NET-Speicherprofilen im Samplingmodus ausführen, verwendet der Profiler Speicherzuteilungsereignisse als Intervall. Er zeigt auch die Gesamtanzahl der zugeteilten Objekte und Bytes als inklusive und exklusive Werte in den Berichten an.

- Wenn Sie die Erstellung des .NET-Speicherprofils im Instrumentierungsmodus ausführen, werden vom Profiler ausführliche Zeitsteuerungsinformationen sowie inklusive und exklusive Zuteilungswerte gesammelt.

[Grundlegendes zu Datenwerte zur Speicherzuteilung und Objektlebensdauer](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Ebeneninteraktion

Bei der Profilerstellung für die Ebeneninteraktion werden einer Profilerstellungsdatendatei Informationen zu synchronen [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]-Aufrufen zwischen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Seite oder einer anderen App und einer [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]-Datenbank hinzugefügt. Die Daten umfassen Anzahl und Zeit der Aufrufe sowie die höchsten und niedrigsten Zeiten. Sie können Ebeneninteraktionsdaten den Profilerstellungsdaten hinzufügen, die Sie mithilfe der Sampling-, Instrumentierungs-, .NET-Speicher- oder Parallelitätsmethode gesammelt haben.

![Datenfluss bei der Profilerstellung für die Ebeneninteraktion](../profiling/media/tierinteraction_profilingtools.png "Datenfluss zur Profilerstellung für die Ebeneninteraktion")

Informationen zu den von den Profilerstellungstools gesammelten Ebeneninteraktionsdaten finden Sie in den folgenden Artikeln.

[Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)

[Ansichten der Ebeneninteraktion](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Sammeln von Leistungsdaten für eine Website](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md)
