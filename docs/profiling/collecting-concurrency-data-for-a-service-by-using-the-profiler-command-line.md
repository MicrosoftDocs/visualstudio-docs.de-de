---
title: 'Profilerbefehlszeile: Abrufen von Parallelitätsdaten für einen Dienst'
description: Dieser Artikel befasst sich mit der Erfassung von Ressourcenkonfliktdaten und Threadaktivitätsdaten mithilfe der Parallelitätsmethode der Profilerstellungstools von Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b4d65490c0ae75c7ab17fd7764d499cb39824f7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148311"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Sammeln von Parallelitätsdaten für einen Dienst über die Profiler-Befehlszeile
Mit der Parallelitätsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie Ressourcenkonfliktdaten und Threadaktivitätsdaten sammeln, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende E/A-Bereiche und andere Systemereignisse geben.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Weitere Informationen finden Sie unter [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Anfügen an einen laufenden .NET-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Parallelitätsdaten](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Anfügen an einen laufenden C/C++-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen nativen Dienst zum Sammeln von Parallelitätsdaten](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-windows-services"></a>Profilerstellung für Windows-Dienste

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Parallelitätsdaten für die Profilerstellung

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung für eigenständige Anwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analysieren von Ansichten und Berichten zu Parallelitätsdaten
- [Ansichten für Ressourcenkonfliktdaten](../profiling/resource-contention-data-views.md)

- [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Verweis
- [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)
