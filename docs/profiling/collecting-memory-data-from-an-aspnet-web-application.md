---
title: 'Profiler-Befehlszeile: Abrufen von Arbeitsspeicherdaten aus einer ASP.NET-Web-App'
description: Hier erfahren Sie, wie Sie mit dem Befehlszeilentool VSPerfCmd Daten zur Speicherbelegung und Objektlebensdauer für eine ASP.NET-Webanwendung sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: edcac130a37b90f164cc2b90c11fe43adeea8414
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949401"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Sammeln von Arbeitsspeicherdaten aus einer ASP.NET-Webanwendung über die Profiler-Befehlszeile
In diesem Abschnitt werden das Vorgehen und Möglichkeiten für das Sammeln von Daten zur Speicherbelegung und Objektlebensdauer für eine ASP.NET-Webanwendung mithilfe des Befehlszeilentools **VSPerfCmd** beschrieben.

> [!NOTE]
> Mit dem Tool **VSPerfCmd** stehen Ihnen sämtliche Funktionen der Profilerstellungstools zur Verfügung, beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor- und Windows-Leistungsindikatoren. Sie können auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden, wenn Sie diese Funktionen nicht benötigen. Anders als beim Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden. Weitere Informationen finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Anfügen des Profilers an eine aktive ASP.NET-Anwendung**|-   [Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Arbeitsspeicherdaten](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentieren statisch kompilierter Binärdateien**|-   [Vorgehensweise: Instrumentieren einer statisch kompilierten ASP.NET-Anwendung und Sammeln von Arbeitsspeicherdaten](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentieren dynamisch kompilierter Binärdateien**|-   [Vorgehensweise: Instrumentieren einer dynamisch kompilierten ASP.NET-Webanwendung und Sammeln von Speicherdaten über die Profiler-Befehlszeile](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profilerstellung für .NET Framework-Arbeitsspeicherdaten

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln von .NET Framework-Arbeitsspeicherdaten](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profilerstellung für Dienste**|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für .NET-Arbeitsspeicherdaten
- [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Verweis
- [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)
