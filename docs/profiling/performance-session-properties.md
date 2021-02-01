---
title: Eigenschaften von Leistungssitzungen | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu Leistungssitzungen. Diese ermöglichen es Ihnen, Einstellungen zu konfigurieren, die bestimmen, wie ein Profil für eine Anwendung erstellt wird.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 02ddf15251cf40dd340465563068b114940f9318
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721228"
---
# <a name="performance-session-properties"></a>Eigenschaften von Leistungssitzungen

Mit einer **Leistungssitzung** können Sie Einstellungen konfigurieren, die bestimmen, wie ein Profil für eine Anwendung erstellt wird. Sie speichert auch Berichte, die für die Profilerstellungssitzung generiert werden.

Erstellen Sie eine **Leistungssitzung** durch Ausführen des **Leistungs-Assistenten** oder durch das manuelle Erstellen einer Sitzung. Die **Leistungssitzung** wird im **Leistungs-Explorer** angezeigt, nachdem die **Leistungssitzung** erstellt wurde.

Wählen Sie den Namen der Sitzung im **Leistungs-Explorer**, klicken Sie mit der rechten Maustaste und wählen Sie dann **Eigenschaften**, um die Eigenschaften der **Leistungssitzung** anzusehen.

Die Leistungssitzung hat folgende Eigenschaftenseiten:

## <a name="general"></a>Allgemein

Mit diesen Einstellungen können Sie die Profilerstellungsmethode auswählen, die .NET-Objektsammlung und Lebenszyklusdaten hinzufügen und den Standardspeicherort und die Benennungskonventionen des Berichts angeben.

Weitere Informationen finden Sie unter

[Vorgehensweise: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)

[Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Starten

Sie können diese Einstellungen aus einer Liste der Binärdateien auswählen und die Startreihenfolge der Binärdateien angeben.

Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der zu startenden Binärdateien](../profiling/how-to-specify-the-binary-to-start.md).

## <a name="sampling"></a>Stichproben

Diese Einstellungen ermöglichen Ihnen die Auswahl des Samplingereignisses und des Samplingintervalls, wenn Sampling als Profilerstellungsmethode verwendet wird. Ein Samplingereignis dient zum Erfassen von Profilerstellungsdaten im angegebenen Intervall. Wenn das Samplingereignis z.B. ein Taktzyklus ist und das Samplingintervall auf 10.000.000 eingestellt ist, werden jeweils nach 10 Millionen Taktzyklen Profilerstellungsdaten erfasst. Die folgenden vier Typen von Samplingereignissen sind verfügbar:

- Taktzyklen: für CPU-Probleme
- Seitenfehler: für Arbeitsspeicherprobleme
- Systemaufrufe: für E/A-Probleme
- Leistungsindikatoren: für Leistungsproblemen auf niedriger Ebene
- Zusätzliche Samplingereignisse können auf Grundlage der verfügbaren Leistungsindikatoren angegeben werden

Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>Binary
Mit diesen Einstellungen können Sie angeben, ob instrumentierte Binärdateien an einen anderen Speicherort verschoben werden sollen. Wenn Sie beispielsweise eine *My.DLL*-Profilerstellung durchführen und die instrumentierte Binärdatei nicht verschieben, wird eine Sicherungskopie von *My.DLL* mit dem Namen *My.Orig.DLL* erstellt. Anschließend wird *My.DLL* geändert, indem Prüfungen zur Datensammlung eingefügt werden. Wenn Sie sich entschließen, die instrumentierte Binärdatei zu verschieben, wird die ursprüngliche Binärdatei nicht umbenannt, und die instrumentierte Binärdatei wird am angegebenen Speicherort zur Verwendung während der Instrumentation kopiert.

Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der zu startenden Binärdateien](../profiling/how-to-specify-the-binary-to-start.md).

## <a name="tier-interactions"></a>Ebeneninteraktionen

Weitere Informationen finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>Instrumentierung

Mit diesen Einstellungen können Sie Leistungsdaten für den JScript-Code in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webseiten sammeln und alle **Präinstrumentations-** und **Postinstrumentationsereignisse** angeben, die vor oder nach dem Instrumentationsprozess ausgeführt werden sollen.

Weitere Informationen finden Sie unter

[Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Vorgehensweise: Festlegen von Präinstrumentations- und Postinstrumentationsbefehlen](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU-Indikatoren

Mit diesen Einstellungen können Sie Daten zu CPU-Leistungsindikatoren sammeln, wenn Sie die Instrumentationsprofilerstellungsmethode verwenden. Portable Leistungszähler sind unabhängig vom CPU-Design und Hersteller verfügbar. Plattformereignisse sind spezifisch für das CPU-Design und den Hersteller. Weitere Informationen über integrierte Leistungsindikatoren finden Sie in der Dokumentation des jeweiligen Prozessors.

Weitere Informationen finden Sie unter [Vorgehensweise: Sammeln von CPU-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows-Ereignisse

Während der Profilierung können Sie Daten von Ereignisablaufverfolgungsanbietern erfassen. Sie können die Daten mithilfe der `/calltrace`-Option des Befehlszeilentools *VSPerfReport.exe* anzeigen. Weitere Informationen über die Ereignisablaufverfolgung für Windows (ETW) finden Sie unter [About Event Tracing (Über Ereignisablaufverfolgung)](/windows/win32/etw/about-event-tracing).

Weitere Informationen finden Sie unter

[Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Windows-Indikatoren

Mit dieser Option können Sie Daten des Windows-Systemmonitors erfassen. Um diese Daten zu sammeln, wählen Sie das Kontrollkästchen **Collect Windows Performance Counters** (Windows-Leistungsindikatoren erfassen) aus. Das Intervall der Datensammlung kann im Feld **Auflistungsintervall** festgelegt werden. **Indikatorenkategorie** und **Instanz** sind möglicherweise auch verfügbar. Einige Standardindikatoren des Windows-Systemmonitors sind verfügbar.

 Weitere Informationen finden Sie unter [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Fortgeschrittene

Mit diesen Einstellungen können Sie die Optionen des Instrumentationsvorgangs hinzufügen, indem Sie eine oder mehrere Optionen des [VSInstr](../profiling/vsinstr.md)-Profilerstellungstools über die Befehlszeile angeben. Wenn die Anwendung mehr als eine Version ausführt, können Sie auch die Version der typischen Laufzeit angeben, für die ein Profil erstellt werden soll.

Weitere Informationen finden Sie unter

[How to: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[How to: Angeben zusätzlicher Instrumentierungsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Siehe auch

[Übersichten (Leistungstools)](../profiling/overviews-performance-tools.md)
[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Steuern der Datensammlung](../profiling/controlling-data-collection.md)
