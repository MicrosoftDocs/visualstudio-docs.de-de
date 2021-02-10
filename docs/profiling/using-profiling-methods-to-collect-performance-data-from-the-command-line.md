---
title: Verwenden von Profilerstellungsmethoden der Befehlszeile zum Sammeln von Leistungsdaten
description: In diesem Artikel erfahren Sie, wie die Auswahl von Profilerstellungstools der Befehlszeilentools in Visual Studio und entsprechende Optionen von Faktoren wie dem Anwendungstyp abhängt, für den Sie ein Profil erstellen.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ebcd3fdbc09029309d1b06efc75417add223ce04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917584"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Verwenden von Profilerstellungsmethoden zum Sammeln von Leistungsdaten über die Befehlszeile
Die zur Verfügung stehenden Befehlszeilentools und Optionen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools hängen von verschiedenen Faktoren ab, beispielsweise von der Art der Anwendung, für die ein Profil erstellt werden soll, von der Profilerstellungsmethode, die Sie verwenden möchten, sowie davon, ob die Zielanwendung in nativem Code oder in .NET Framework-Code geschrieben ist.

 In diesem Thema sind die Themen über Verfahren mittels Befehlszeile gemäß der ausgewählten Profilerstellungsmethode aufgeführt.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Verwenden der Samplingmethode zum Sammeln von Leistungsstatistiken
 Mit der Samplingmethode der Profilerstellungstools werden während einer Profilerstellung Leistungsdaten in angegebenen Intervallen gesammelt. Samplingdaten ermöglichen Einblicke in Leistungsprobleme im Zusammenhang mit der CPU, und sie ermöglichen eine Basis für die Untersuchung der Leistung einer Anwendung.

 Sie können gleichzeitig den Profiler und die Anwendung starten oder den Profiler an eine Instanz einer Anwendung anfügen, die gerade ausgeführt wird.

|Aufgabe|Art der Zielanwendung|
|----------|-----------------------------|
|**Starten einer Anwendung**|-   [Eigenständige Anwendungen](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Anfügen an einen laufenden Prozess**|-   [Eigenständige .NET Framework-Anwendungen](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Native, eigenständige Anwendungen](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET-Webanwendungen](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET-Dienste](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Native Dienste](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Sammeln von ausführlichen Zeitsteuerungsdaten mit der Instrumentierungsmethode
 Mit der Instrumentierungsmethode der Profilerstellungstools werden Leistungsdaten aus Kopien von Anwendungsbinärdateien gesammelt, die Softwaretests zum Erfassen von Leistungsinformationen enthalten. Instrumentierungsdaten werden am Anfang und Ende jeder instrumentierten Funktion und jedes Aufrufs von anderen Funktionen durch die instrumentierte Funktion gesammelt. Die Instrumentierungsmethode ist nützlich für das Ermitteln von Leistungsbeeinträchtigungen aufgrund von E/A-Problemen, z.B. bei der Datenträgerverwendung.

 Die instrumentierte Binärdatei wird mit dem Tool [VInstr.exe](../profiling/vsinstr.md) erstellt. Nachdem Sie den Profiler initialisiert haben, werden die Daten automatisch von den instrumentierten Binärdateien gesammelt, wenn Sie die Zielanwendung ausführen.

 **Art der Zielanwendung**

- [Eigenständige .NET Framework-Komponenten](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Native, eigenständige Komponenten](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Statisch kompilierte ASP.NET-Webanwendungen](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dynamisch kompilierte ASP.NET-Webanwendungen](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET-Dienste](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Native Dienste](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Verwenden von .NET-Arbeitsspeichermethoden zur Sammlung von Daten zur Speicherbelegung und Objektlebensdauer
 Die .NET-Arbeitsspeichermethode der Profilerstellungstools ermöglicht das Sammeln von Speicherbelegungsdaten für .NET Framework sowie von Informationen zur Lebensdauer von Objekten in .NET Framework.

 Sie können die Zielanwendung mit dem Profiler starten, den Profiler an eine aktive Instanz einer Anwendung anfügen und instrumentierte Versionen der Anwendung erstellen, um ausführliche Zeitsteuerungsinformationen sowie .NET Framework-Speicherdaten zu sammeln.

|Aufgabe|Art der Zielanwendung|
|----------|-----------------------------|
|**Starten einer Anwendung**|-   [Eigenständige .NET Framework-Anwendungen](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Anfügen an einen laufenden Prozess**|-   [Eigenständige .NET Framework-Anwendungen](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET-Webanwendungen](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET-Dienste](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentieren von Modulen**|-   [Eigenständige .NET Framework-Komponenten](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statisch kompilierte ASP.NET-Webanwendungen](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dynamisch kompilierte ASP.NET-Webanwendungen](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET-Dienste](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Erfassen von Daten zu Ressourcenkonflikten und Threadaktivitäten mit der Parallelitätsmethode
 Mit der Nebenläufigkeitsmethode der Profilerstellungstools können Sie Daten zu Ressourcenkonflikten sowie zu Thread- und Prozessaktivitäten aus Anwendungen mit mehreren Threads sammeln.

 Sie können die Anwendung mit dem Profiler starten oder den Profiler an eine Instanz einer Anwendung anfügen, die gerade ausgeführt wird.

|Aufgabe|Art der Zielanwendung|
|----------|-----------------------------|
|**Starten einer Anwendung**|-   [Eigenständige .NET Framework-Anwendung](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Native eigenständige Anwendung](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Anfügen an einen laufenden Prozess**|-   [Eigenständige .NET Framework-Anwendung](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Native, eigenständige Anwendung](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET-Webanwendung](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET-Dienst](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Nativer Dienst](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung
 Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
