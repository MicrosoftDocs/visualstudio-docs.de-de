---
title: CPU- und Windows-Indikatoren | Microsoft-Dokumentation
description: CPU- (Hardware) und Windows-Zähler (Software) liefern Leistungsdaten. Hier erfahren Sie, wie Sie sie anzeigen können, und wie dazugehörige Daten erfasst werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c3657f3558a688232424b868d0e93b8c056467c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719161"
---
# <a name="cpu-and-windows-counters"></a>CPU- und Windows-Indikatoren

Der Visual Studio-Profiler ermöglicht das Sammeln von Leistungsdaten, die vom Betriebssystem (Windows-Indikatoren) generiert wurden, und Leistungsdaten, die von der Prozessoreinheit (CPU-Indikatoren) generiert wurde.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Windows-Indikatoren

Windows-Indikatoren sind Teil der Windows-Diagnoseinfrastruktur, die Informationen über die Leistung des Betriebssystems oder einer Anwendung, einen Dienst oder einen Treiber bereitstellt. Windows-Indikatoren hängen von der Konfiguration des aktuellen Computers ab und sind unter Umständen nicht auf anderen Computern verfügbar. Windows-Leistungsindikatoren werden in Profilerstellungsdatendateien als Profilerstellungsmarkierungen gesammelt, die sich zum Filtern von Ansichten und Berichten verwenden lassen.

## <a name="cpu-counters"></a>CPU-Indikatoren

CPU-Indikatoren sind eine Funktion der Computer-CPU und speichern die Anzahl der hardwarebezogenen Ereignisse. Wenn Sie CPU-Indikatordaten mithilfe der Profilerstellungsmethode zur Instrumentation sammeln, werden diese Daten an die Daten für Funktionen und Module angefügt. Sie können mehrere CPU-Indikatoren mit der Instrumentationsmethode sammeln. Wenn Sie die Samplingmethode verwenden, wählen Sie einen Indikator aus, der als zu überprüfendes Ereignis verwendet werden soll.

Leistungsindikatoren sind CPU-spezifisch. Unterschiedliche CPU-Modelle und -Versionen können deutlich abweichende Konfigurationseinstellungen für denselben Leistungsindikator aufweisen. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Übertragbare Profiler-Ereignisse entkoppeln einige gängige Leistungsindikatoren von bestimmten Prozessoren und ermöglichen es Ihnen, allgemeine Leistungsereignisse zu sammeln oder ein Sampling für sie durchzuführen.

Wenn Sie bei der Verwendung des Profilers ein bestimmtes Ereignis wie z.B. E2-Cachefehler berücksichtigen möchten, können Sie eine Leistungssitzung für den Absender des Ereignisses erstellen. Dies ist für jede CPU mit einem L2-Cache möglich. Die Leistungssitzung kann ohne weitere Änderung zwischen Plattformen verschoben werden.

Visual Studio-Profiler unterstützt weiterhin bestimmte Ereignisse für eine bestimmte Plattform. So kann beispielsweise ein Entwickler auf einer Pentium 4-Plattform die Ereignisse erfassen, die spezifisch für die NetBurst-Architektur sind. Dieses Ereignis ist zwar nicht übertragbar, steht jedoch weiterhin dem Entwickler für eine spezifische Leistungssitzung auf einer bestimmten Plattform zur Verfügung.

## <a name="portable-and-platform-events"></a>Übertragbare Ereignisse und Plattformereignisse

Bei übertragbaren Ereignissen handelt es sich um eine Gruppe von CPU-Indikatoren, die nicht spezifisch für einen bestimmten Prozessor sind. Alle anderen CPU-Indikatoren werden als Plattformereignisse bezeichnet, die möglicherweise auf verschiedenen Plattformen nicht unterstützt werden.

 Indikatoren für übertragbare Ereignisse und Plattformereignisse werden in *XML*-Dateien definiert, die auch bestimmte Werte in Bezug auf die Indikatoren enthalten. Da die Daten für Intel- und AMD-CPUs beispielsweise unterschiedlich sind, werden mehrere Dateien für die verschiedenen CPUs bereitgestellt. Der [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]-Profiler nutzt diese Informationen, um dem Benutzer für Leistungsmessungen die geeigneten Indikatoren – sowohl portable Indikatoren als auch Plattformindikatoren – zur Verfügung zu stellen.

### <a name="portable-events"></a>Übertragbare Ereignisse

Übertragbare Ereignisse enthalten die folgenden Ereignisse:

**Allgemeine Ereignisse**

|Ereignisname|Ereignisbeschreibung|
|----------------|-----------------------|
|Zurückgezogene Anweisungen|Gibt die Anzahl von Anweisungen an, die bis zum Abschluss des Ereignisses ausgeführt wurden|
|Nicht angehaltene Zyklen|Gibt nur diejenigen Zyklen an, in denen der Prozessor nicht angehalten wird, z.B. weil auf E/A gewartet wird|

**Front-End-Ereignisse**

|Ereignisname|Ereignisbeschreibung|
|----------------|-----------------------|
|ITLB-Fehler|Gibt die Anzahl der ITLB-Suchen (Instruction Translation Lookaside Buffer) an, die zu einem Fehler führten|

**Verzweigungsereignisse**

|Ereignisname|Ereignisbeschreibung|
|----------------|-----------------------|
|Zurückgezogene Verzweigungen|Gibt die Anzahl der Verzweigungsanweisungen an, die bis zum Abschluss des Ereignisses ausgeführt wurden|
|Falsch vorhergesagte Verzweigungen|Gibt falsch vorhergesagte Verzweigungen an, zu denen es kommt, weil der Prozessor einen falschen Pfad vorhergesagt hat. Falsch vorhergesagte Verzweigungen führen zu Leistungseinbußen, weil der Prozessor alle bereits ausgeführten Arbeiten verwerfen und mit einem korrekten Pfad erneut starten muss.|

**Speicherereignisse**

|Ereignisname|Ereignisbeschreibung|
|----------------|-----------------------|
|E2-Cachelesefehler|Gibt die Anzahl der Lesefehler im Cache der 2. Ebene an|
|E2-Cacheleseverweise|Gibt die Anzahl der Leseverweise im Cache der 2. Ebene an. Dies schließt Ladefehler sowie RFO-Fehler und -Treffer (Read For Ownership) ein.|

## <a name="view-available-counters"></a>Anzeigen verfügbarer Indikatoren

Sie können die verfügbaren CPU-Indikatoren in der Visual Studio-IDE in einem Eingabeaufforderungsfenster aufführen.

### <a name="visual-studio-ui"></a>Visual Studio-Benutzeroberfläche

Zum Auflisten der verfügbaren Indikatoren auf einem Computer in der Visual Studio-IDE benötigen Sie eine Profiler-Leistungssitzung, die im Leistungs-Explorer geöffnet ist.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>So zeigen Sie eine Liste aller CPU-Indikatoren an, die auf der aktuellen Plattform unterstützt werden

1. Klicken Sie im Leistungs-Explorer mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.

2. Führen Sie einen der folgenden Schritte aus:

   - Klicken Sie auf **Sampling**, und wählen Sie anschließend aus der Ereignisliste **Beispiel** die Option **Leistungsindikator** aus. Die CPU-Indikatoren werden unter **Verfügbare Leistungsindikatoren** aufgeführt.

      **Hinweis** Klicken Sie auf **Abbrechen**, um zur vorherigen Samplingkonfiguration zurückzukehren.

     - oder -

   - Wählen Sie **CPU-Indikatoren** und anschließend **CPU-Indikatoren auflisten** aus. Die CPU-Indikatoren werden unter **Verfügbare Indikatoren** aufgeführt.

      **Hinweis** Klicken Sie auf **Abbrechen**, um zur vorherigen Konfiguration der Leistungsindikatorauflistung zurückzukehren.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>So zeigen Sie eine Liste aller Windows-Indikatoren an, die auf der aktuellen Plattform unterstützt werden

1. Klicken Sie im Leistungs-Explorer mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.

2. Klicken Sie auf **Windows-Indikatoren**.

3. Wählen Sie **Windows-Indikatoren auflisten** aus.

4. Wählen Sie aus der Liste **Indikatorkategorie** eine Gruppe von Leistungsindikatoren aus. Der Windows-Leistungsindikator für die Gruppe wird im Listenfeld angezeigt.

     **Hinweis**: Klicken Sie auf **Abbrechen**, um zur vorherigen Konfiguration der Leistungsindikatorsammlung zurückzukehren.

### <a name="command-line"></a>Befehlszeile

Mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) können Sie die auf einem Computer verfügbaren CPU-Indikatoren in der Befehlszeile aufführen.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>So führen Sie die CPU-Indikatoren auf, die auf der aktuellen Plattform unterstützt werden

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Typ

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**

     Dabei ist *\<Visual Studio Performance Tools Directory>* der Pfad zum Performance Tools-Verzeichnis der Visual Studio-Installation. Informationen zum Abrufen des Pfads zu den Leistungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Siehe auch

- [Übersichten](../profiling/overviews-performance-tools.md)
- [How to: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)
- [How to: Sammeln von CPU-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)
- [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)
