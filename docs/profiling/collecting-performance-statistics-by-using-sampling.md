---
title: Sammeln von Leistungsstatistiken durch Sampling
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9729bf46b58a9591df7b6470acde0c54ef23f531
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810730"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Sammeln von Leistungsstatistiken durch Sampling

Standardmäßig werden Profilinformationen durch die Samplingmethode der Visual Studio-Profilerstellungstools alle 10.000.000 Prozessorzyklen erfasst (ungefähr jede Hundertstelsekunde auf einem 1-GHz-Computer). Die Samplingmethode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Zum Angeben der Samplingmethode haben Sie folgende Möglichkeiten:

- Klicken Sie auf der ersten Seite des Profilerstellungs-Assistenten auf **CPU-Sampling (empfohlen)** .
- Klicken Sie in der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Sampling**.
- Klicken Sie im Eigenschaftendialogfeld der Leistungssitzung auf der Seite **Allgemein** auf **Sampling**.

## <a name="common-tasks"></a>Allgemeine Aufgaben

Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld

- Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

  Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie ein Profil mithilfe der Samplingmethode erstellen.

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|Fügen Sie auf der Seite **Allgemein** gesammelte Daten zur .NET-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|- [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [How to: Set Performance Data File Name Option (Vorgehensweise: Festlegen von Dateinamenoptionen für Profilerstellungsdaten)](../profiling/how-to-set-performance-data-file-name-options.md)|
|Ändern Sie auf der Seite **Sampling** die Samplingrate, ändern Sie das Samplingereignis von Prozessortaktzyklen in einen anderen Prozessorleistungsindikator, oder ändern Sie beide Werte.|- [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)|
|Wenn sich in der Codeprojektmappe mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|- [Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE](../profiling/collecting-tier-interaction-data.md)|
|Fügen Sie auf der Seite **Ebeneninteraktionen** ADO.NET-Aufrufinformationen zu den Daten hinzu, die während der Profilerstellung gesammelt wurden.|- [Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE](../profiling/collecting-tier-interaction-data.md)|
|Geben Sie auf der Seite **Windows-Ereignisse** ein oder mehrere ETW-Ereignisse (Ereignisse der Ereignisablaufverfolgung für Windows) an, die mit den Samplingdaten erfasst werden sollen.|- [Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|- [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden. Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|- [How to: Specify the .NET Framework Runtime (Vorgehensweise: Angeben der .NET Framework-Laufzeit)](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
