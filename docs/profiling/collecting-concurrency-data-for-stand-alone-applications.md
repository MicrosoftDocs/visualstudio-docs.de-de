---
title: 'Profilerbefehlszeile: Abrufen von Parallelitätsdaten einer eigenständigen App'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1d49ffdca054034e1ec08105d2041794714bcdee
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811122"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Sammeln von Parallelitätsdaten für eigenständige Anwendungen über die Profiler-Befehlszeile
Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Starten einer .NET Framework-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Vorgehensweise: Starten einer eigenständigen .NET Framework-Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Starten einer C/C++-Anwendung und Profilerstellung von Parallelitätsdaten**|-   [Vorgehensweise: Starten einer nativen, eigenständigen Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Anfügen des Profilers an eine aktive .NET Framework-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Anfügen des Profilers an eine aktive C/C++-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine native, eigenständige Anwendung und Sammeln von Parallelitätsdaten über die Befehlszeile](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET Framework-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Parallelitätsprobleme bei der Profilerstellung

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profilerstellung für Dienste**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analysieren von Ansichten und Berichten zu Parallelitätsdaten
- [Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)

- [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Verweis
- [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)
