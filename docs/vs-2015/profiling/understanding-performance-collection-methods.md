---
title: Grundlagen zu Leistungserfassungsmethoden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e398d7e5e297daa68663902efb8a9fa0775c86fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840895"
---
# <a name="understanding-performance-collection-methods"></a>Grundlagen zu Leistungserfassungsmethoden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Von den Profilerstellungstools für Visual Studio werden fünf Methoden zum Sammeln von Leistungsdaten bereitgestellt. In diesem Thema werden die verschiedenen Methoden beschrieben sowie einige Szenarien aufgeführt, in denen die Datensammlung mithilfe einer bestimmten Methode erfolgen kann.  
  
> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Sampling](#sampling)|Sammelt statistische Daten zu den von einer Anwendung ausgeführten Aufgaben.|  
|[Instrumentierung](#instrumentation)|Dient zum Sammeln ausführlicher Zeitsteuerungsinformationen zu den einzelnen Funktionsaufrufen.|  
|[Parallelität](#concurrency)|Dient zum Sammeln ausführlicher Informationen zu Multithreadanwendungen.|  
|[.NET-Arbeitsspeicher](#net_memory)|Dient zum Sammeln ausführlicher Informationen zur .NET-Speicherbelegung und zur Garbage Collection.|  
|[Ebeneninteraktion](#tier_interaction)|Sammelt Informationen zu synchronen, an eine SqlServer-Datenbank gerichteten ADO.NET-Funktionsaufrufen.<br /><br /> Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] angezeigt werden.|  
  
 Mit einigen Profilerstellungsmethoden können auch weitere Daten gesammelt werden, z. B. Software- und Hardwareleistungsindikatoren. Weitere Informationen finden Sie unter [Sammeln zusätzlicher Leistungsdaten](../profiling/collecting-additional-performance-data.md).  
  
## <a name="sampling"></a><a name="sampling"></a> Stichprobenentnahme  
 Bei der Samplingmethode für die Profilerstellung werden statistische Daten zu den Aufgaben gesammelt, die während einer Profilerstellung von einer Anwendung ausgeführt wurden. Die Samplingmethode ist einfach und wirkt sich kaum auf die Ausführung der Anwendungsmethoden aus.  
  
 Das Sampling ist die Standardmethode der Profilerstellungstools von Visual Studio. Es eignet sich für folgende Zwecke:  
  
- Erstuntersuchung der Anwendungsleistung  
  
- Untersuchung von Leistungsproblemen, die die Auslastung des Prozessors (CPU) betreffen  
  
  Bei der Samplingmethode für die Profilerstellung wird der Prozessor des Computers in festgelegten Abständen unterbrochen, und die Funktionsaufrufliste wird erfasst. Der Wert für exklusive Samplings wird für die ausgeführte Funktion, der Wert für inklusive Samplings für alle aufrufenden Funktionen aus der Aufrufliste erhöht. Samplingberichte enthalten die Gesamtwerte für das Modul, die Funktion, die Quellcodezeile und die Anweisung, für die das Profil erstellt wurde.  
  
  Das Samplingintervall wird vom Profiler standardmäßig auf CPU-Zyklen festgelegt. Sie können den Intervalltyp auf einen anderen CPU-Leistungsindikator sowie die Anzahl der Leistungsindikatorereignisse für das Intervall festlegen. Darüber hinaus können Sie auch Profilerstellungsdaten für die Ebeneninteraktion (TIP-Daten) sammeln, die Aufschluss über die Abfragen geben, die über ADO.NET an eine SQL Server-Datenbank gestellt wurden.  
  
  [Collecting Performance Statistics by Using Sampling (Sammeln von Leistungsstatistiken durch Sampling)](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [Grundlegendes zu Stichprobendaten Werten](../profiling/understanding-sampling-data-values.md)  
  
  [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)  
  
## <a name="instrumentation"></a><a name="instrumentation"></a> Ener  
 Bei der Instrumentierungsmethode zur Profilerstellung werden ausführliche Zeitsteuerungsinformationen für die Funktionsaufrufe in der Anwendung gesammelt, für die das Profil erstellt wird. Mögliche Anwendungsbereiche der instrumentierten Profilerstellung:  
  
- Untersuchung von Eingabe/Ausgabe-Engpässen (beispielsweise Datenträger-E/A)  
  
- Gründliche Untersuchung eines bestimmten Moduls oder einer bestimmten Gruppe von Funktionen  
  
  Bei der Instrumentationsmethode wird Code in eine Binärdatei eingefügt, um Zeitsteuerungsinformationen zu den einzelnen Funktionen in der instrumentierten Datei sowie alle von diesen Funktionen ausgeführten Funktionsaufrufe zu erfassen. Mit der Instrumentation werden für Vorgänge wie dem Schreiben einer Datei auch Aufrufe des Betriebssystems durch eine Funktion identifiziert. Die Gesamtzeit, die für eine Funktion oder für eine Quellcodezeile aufgewendet wurde, wird in den Instrumentationsberichten mithilfe von vier Werten dargestellt:  
  
- Verstrichene inklusive Zeit: Die Gesamtzeit, die für das Ausführen der Funktion oder Quellcodezeile aufgewendet wurde.  
  
- Inklusive Anwendungszeit: Die Zeit, die für das Ausführen der Funktion oder Quellcodezeile aufgewendet wurde, aber ohne die Zeit für Aufrufe des Betriebssystems.  
  
- Verstrichene exklusive Zeit: Die Zeit, die für das Ausführen von Code im Funktionstext oder in der Quellcodezeile aufgewendet wurde. Die Zeit für das Ausführen von Funktionen, die von der Funktion oder von der Quellcodezeile aufgerufen wurden, wird nicht einbezogen.  
  
- Exklusive Anwendungszeit: Die Zeit, die für das Ausführen von Code im Funktionstext oder in der Quellcodezeile aufgewendet wurde. Die Zeit für das Ausführen von Aufrufen des Betriebssystems sowie für das Ausführen der Funktionen, die von der Funktion oder von der Quellcodezeile aufgerufen wurden, wird nicht einbezogen.  
  
  Mithilfe der Instrumentierungsmethode können auch CPU- sowie Softwareleistungsindikatoren gesammelt werden.  
  
  [Grundlegendes zu Instrumentations Datenwerten](../profiling/understanding-instrumentation-data-values.md)  
  
  [Collecting Detailed Timing Data by Using Instrumentation (Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung) ](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [Instrumentierungsmethoden-Datenansichten](../profiling/instrumentation-method-data-views.md)  
  
## <a name="concurrency"></a><a name="concurrency"></a> Concurrency  
 Bei der Parallelitätsprofilerstellung werden Informationen zu Multithreadanwendungen gesammelt. Bei der Profilerstellung für Ressourcenkonflikte werden immer dann ausführliche Aufruflisteninformationen gesammelt, wenn von konkurrierenden Threads auf den Zugriff auf eine freigegebene Ressource gewartet werden muss. Bei der Parallelitätsschnellansicht werden zusätzlich allgemeinere Informationen zur Interaktion der Multithreadanwendung mit sich selbst, der Hardware, dem Betriebssystem und anderen Prozessen auf dem Hostcomputer gesammelt:  
  
- Ressourcenkonfliktberichte enthalten für die Module, Funktionen, Quellcodezeilen und Anweisungen, in denen die Verzögerung aufgetreten ist, die Gesamtanzahl von Konflikten sowie die Gesamtwartezeit für eine Ressource. Die aufgetretenen Konflikte werden zudem in Zeitachsendiagrammen dargestellt.  
  
- In der Parallelitätsschnellansicht werden grafische Informationen angezeigt, die Sie verwenden können, um Leistungsengpässe, CPU-Unterauslastungen, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, Bereiche überlappender E/A und andere Informationen zu suchen. Gegebenenfalls wird die grafische Ausgabe mit Aufruflisten- und Quellcodedaten verknüpft. Die Daten für die Parallelitätsschnellansicht können nur für Befehlszeilen- und Windows-Anwendungen gesammelt werden.  
  
  [Grundlegendes zu Ressourcen Konflikt-Datenwerten](../profiling/understanding-resource-contention-data-values.md)  
  
  [Collecting Thread and Process Concurrency Data (Sammeln von Nebenläufigkeitsdaten zu Threads und Prozessen) ](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [Datenansichten von Ressourcenkonflikten](../profiling/resource-contention-data-views.md)  
  
  [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)  
  
## <a name="net-memory"></a><a name="net_memory"></a> .NET-Speicher  
 Bei der .NET-Speicherbelegungsmethode zur Profilerstellung wird der Prozessor des Computers bei jeder Belegung eines .NET Framework-Objekts in einer Anwendung unterbrochen, für die das Profil erstellt wird. Wenn auch Objektlebensdauerdaten erfasst werden, unterbricht der Profiler den Prozessor nach jeder .NET Framework-Garbage Collection.  
  
 Vom Profiler werden Informationen zu Typ, Größe und Anzahl der Objekte gesammelt, die bei einer Speicherbelegung erstellt oder bei einer Garbage Collection zerstört wurden.  
  
- Bei Auftreten eines Speicherbelegungsereignisses werden weitere Informationen zur Funktionsaufrufliste gesammelt. Der Wert für exklusive Zuordnungen wird für die derzeit ausgeführte Funktion, der Wert für inklusive Zuordnungen für alle aufrufenden Funktionen aus der Aufrufliste erhöht. .NET-Berichte enthalten die Gesamtwerte für die Typen, Module, Funktionen, Quellcodezeilen und Anweisungen, für die das Profil erstellt wurde.  
  
- Bei Auftreten einer Garbage Collection werden vom Profiler Daten zu den zerstörten Objekten sowie Informationen zu den Objekten in den einzelnen Garbage Collection-Generationen gesammelt. Am Ende der Profilerstellung werden Daten zu den Objekten erfasst, die nicht explizit zerstört wurden. Der Bericht Objektlebensdauer enthält die Gesamtwerte für jeden Typ, der im Rahmen der Profilerstellung belegt wurde.  
  
  Die .NET-Speicherprofilerstellung kann sowohl im Sampling- als auch im Instrumentationsmodus verwendet werden. Der gewählte Modus besitzt keine Auswirkungen auf die Berichte zur Speicherbelegung oder zur Objektlebensdauer, die für die .NET-Speicherprofilerstellung spezifisch sind:  
  
- Wenn Sie die .NET-Speicherprofilerstellung im Samplingmodus ausführen, werden .NET Speicherbelegungsereignisse als Intervall verwendet. Darüber hinaus werden in den Berichten die Anzahl der belegten Objekte sowie die Gesamtanzahl der belegten Bytes als inklusive und exklusive Werte angezeigt.  
  
- Wenn Sie die .NET-Speicherprofilerstellung im Instrumentierungsmodus ausführen, werden ausführliche Zeitsteuerungsinformationen sowie inklusive und exklusive Speicherbelegungswerte gesammelt.  
  
  [Grundlegendes zu Datenwerten für Speicher Belegung und Objekt Lebensdauer](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [.NET-Arbeitsspeicher Datenansichten](../profiling/dotnet-memory-data-views.md)  
  
## <a name="tier-interaction"></a><a name="tier_interaction"></a> Ebeneninteraktion  
 Bei der Profilerstellung für die Ebeneninteraktion werden einer Profilerstellungsdatendatei Informationen zu synchronen [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Aufrufen zwischen einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Seite oder einer anderen Anwendung und einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank hinzugefügt. Die Daten umfassen Anzahl und Zeit der Aufrufe sowie die höchsten und niedrigsten Zeiten. Ebeneninteraktionsdaten können den Profilerstellungsdaten hinzugefügt werden, die mithilfe der Sampling-, Instrumentierungs-, .NET-Speicher- oder Parallelitätsmethode gesammelt wurden.  
  
 ![Profilerstellungsdaten für die Ebeneninteraktion](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
Von den Profilerstellungstools gesammelte Ebeneninteraktionsdaten  
  
 [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/collecting-tier-interaction-data.md)  
  
 [Ebeneninteraktions-Ansicht](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Erfassen von Leistungsdaten für eine Website](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Einführung in die Leistungsprofil Erstellung](../profiling/beginners-guide-to-performance-profiling.md)
