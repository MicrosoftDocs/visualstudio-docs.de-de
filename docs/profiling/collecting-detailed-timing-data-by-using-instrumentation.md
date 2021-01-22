---
title: Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung
description: Verwenden Sie die Instrumentierungsmethode der Profilerstellungstools, um detaillierte Zeitangaben für einen Abschnitt Ihres Codes zu erhalten und die Auswirkungen von E/A-Vorgängen zu verstehen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17c569a9f5a50b769af0881d47fe810afe18058e
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533848"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung
Bei der Instrumentationsmethode der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Profilerstellungstools wird Profilerstellungscode in eine Kopie eines Moduls eingefügt. Der Code zeichnet während der Profilerstellung jeden Funktionseinstieg, jedes Funktionsende und jeden Funktionsaufruf im Modul auf. Mithilfe der Instrumentationsmethode können ausführliche Zeitsteuerungsdaten zu einem Abschnitt des Codes erfasst werden. Zudem werden mit dieser Methode die Auswirkungen von Eingabe- und Ausgabeoperationen auf die Leistung der Anwendung besser verständlich.

 Sie können die Instrumentationsmethode mit einem der folgenden Verfahren angeben:

- Wählen Sie auf der ersten Seite des Profilerstellungs-Assistenten **Instrumentation** aus.

- Klicken Sie auf der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Instrumentation**.

- Wählen Sie auf der Seite **Allgemein** im Dialogfeld „Eigenschaften“ für die Leistungssitzung **Instrumentation** aus.

## <a name="common-tasks"></a>Allgemeine Aufgaben
 Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld

- Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

  Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie die Profilerstellung mit der Instrumentationsmethode ausführen.

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|Fügen Sie auf der Seite **Allgemein** Daten zur .NET-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|-   [Sammeln von Daten zur .NET-Speicherbelegung und -lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|
|Wenn sich in der Projektmappe mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|-   [Vorgehensweise: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|
|Geben Sie auf der Seite **Binärdateien** einen Speicherort für die instrumentierten Kopien der Module an. Standardmäßig werden die ursprünglichen Binärdateien in einen Sicherungsordner verschoben.|-   [Vorgehensweise: Verschieben instrumentierter Binärdateien](../profiling/how-to-relocate-instrumented-binaries.md)|
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktion** ADO.NET-Aufrufdaten hinzu.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|
|Schließen Sie auf der Seite **Instrumentation** kleine Funktionen von der Profilerstellung aus, um den Profilerstellungsaufwand zu reduzieren, erstellen Sie für JavaScript-Code in ASP.NET-Webseiten ein Profil, und geben Sie Befehle an, die vor und nach der Instrumentation über eine Eingabeaufforderung ausgeführt werden sollen.|-   [Vorgehensweise: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Vorgehensweise: Festlegen von Präinstrumentations- und Postinstrumentationsbefehlen](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Geben Sie auf der Seite **CPU-Indikatoren** einen oder mehrere Prozessorleistungsindikatoren an, die den Profilerstellungsdaten hinzugefügt werden sollen.|-   [Vorgehensweise: Sammeln von CPU-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)|
|Wählen Sie auf der Seite **Windows-Ereignisse** ein oder mehrere ETW-Ereignisse (Ereignisse der Ereignisablaufverfolgung für Windows) aus, die mit den Samplingdaten erfasst werden sollen.|-   [Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|
|Geben Sie auf der Seite **Erweitert** zusätzliche Optionen an, die Sie an das VSInstr-Instrumentationsprogramm übergeben möchten, z. B. Optionen zum Ein- oder Ausschließen bestimmter Funktionen.|-   [Vorgehensweise: Angeben zusätzlicher Instrumentierungsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Vorgehensweise: Einschränken der Instrumentierung auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
