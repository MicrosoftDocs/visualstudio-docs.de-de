---
title: Sammeln paralleler Daten für eigenständige Anwendungen über die Profiler-Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141933"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Sammeln paralleler Daten für eigenständige Anwendungen über die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Starten einer .NET Framework-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Gewusst wie: Starten einer .NET Framework Anwendung zum Sammeln von Parallelitäts Daten](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Starten einer C/C++-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Vorgehensweise: Starten einer nativen, eigenständigen Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Anfügen des Profilers an eine aktive .NET Framework-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Anfügen des Profilers an eine aktive C/C++-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine native, eigenständige Anwendung und Sammeln paralleler Daten über die Befehlszeile](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
### <a name="profiling-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeit Steuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET Framework-Speicherdaten für eigenständige Anwendungen über die Profiler-Befehlszeile](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilerstellung bei Parallelitätsproblemen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analysieren von Parallelitätsdatenansichten und -berichten  
 [Datenansichten von Ressourcenkonflikten](../profiling/resource-contention-data-views.md)  
  
 [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referenz  
 [Befehlszeilen Profilerstellungstools Referenz](../profiling/command-line-profiling-tools-reference.md)
