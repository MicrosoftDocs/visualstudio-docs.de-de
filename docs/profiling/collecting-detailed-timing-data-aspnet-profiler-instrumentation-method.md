---
title: Abrufen von Zeitsteuerungsdaten für ASP.NET mithilfe der Instrumentierung
description: Hier erfahren Sie, wie Sie mit VSPerfCmd detaillierte Leistungsdaten für eine ASP.NET-Webanwendung erfassen. Das Tool bietet Vollzugriff auf die Funktionalität der Profilerstellungstools.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: c0eca3aa29795da4a2d1233f0cba1774641fc364
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868321"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Sammeln ausführlicher Zeitsteuerungsdaten für eine ASP.NET-Webanwendung über die Befehlszeile mit der Profiler-Instrumentierungsmethode
In diesem Abschnitt werden die Prozeduren und die Optionen zum Sammeln ausführlicher Leistungsdaten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung unter Verwendung der Instrumentationsmethode und der Befehlszeile **VSPerfCmd** beschrieben.

> [!NOTE]
> Mit dem Tool **VSPerfCmd** stehen Ihnen sämtliche Funktionen der Profilerstellungstools zur Verfügung, beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor- und Windows-Leistungsindikatoren. Sie können auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden, wenn Sie diese Funktionen nicht benötigen. Verglichen mit dem [VSPerfCmd](../profiling/vsperfcmd.md)-Befehlszeilentool stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und ein Neustart des Computers ist nicht erforderlich. Weitere Informationen finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profile statically compiled binaries (Erstellen eines Profils für statisch kompilierte Binärdateien)**|-   [Vorgehensweise: Instrumentieren einer statisch kompilierten ASP.NET-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profile dynamically compiled binaries (Erstellen eines Profils für dynamisch kompilierte Binärdateien)**|-   [Vorgehensweise: Instrumentieren einer dynamisch kompilierten ASP.NET-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilerstellung der Speicherbelegung und Garbage Collection**|-   [Sammeln von Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Profilerstellung mit der Instrumentierungsmethode

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profilerstellung für Dienste**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Analysieren von Instrumentierungsdatenansichten und -berichten
- [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)
