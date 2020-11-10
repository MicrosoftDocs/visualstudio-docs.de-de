---
title: Erste Schritte mit Profilerstellungstools
description: Einführung in die verschiedenen für Visual Studio verfügbaren Diagnosetools
ms.custom: ''
ms.date: 09/08/2020
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 849b9d7bd6aca3fa56cb0106bea844ce1fa56b73
ms.sourcegitcommit: ae9145b32fc8e1e663e504c315a5df5dd302fee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92918239"
---
# <a name="first-look-at-profiling-tools"></a>Einführung in Profilerstellungstools

Visual Studio bietet eine Vielzahl von Profilerstellungstools, um Ihnen bei der Diagnose von unterschiedlichen Leistungsprobleme zu helfen, die von dem App-Typ abhängen. In diesem Artikel werfen wir einen kurzen Blick auf die gängigsten Profilerstellungstools.

Informationen zur Unterstützung der Profilerstellungstools für die verschiedenen App-Typen finden Sie unter [Welches Tool soll ich verwenden?](#which-tool-should-i-use).

## <a name="measure-performance-while-debugging"></a>Messen der Leistung beim Debuggen

Die Profilerstellungstools, auf die Sie während einer Debugsitzung zugreifen können, stehen im Fenster „Diagnosetools“ zur Verfügung. Das Fenster „Diagnosetools“ wird automatisch angezeigt, wenn Sie es nicht deaktiviert haben. Klicken Sie auf **Debuggen/Windows/Diagnosetools anzeigen** , um das Fenster aufzurufen. Wenn das Fenster geöffnet ist, können Sie Tools auswählen, für die Sie Daten sammeln möchten.

![Fenster „Diagnosetools“](../profiling/media/prof-tour-diagnostic-tools.png "Diagnosetools")

Während Sie Debuggen, können Sie das **Diagnosetools** -Fenster zum Analysieren der CPU und Speicherauslastung verwenden, und Sie können Ereignisse anzeigen, die Leistungsbezogene Informationen zeigen.

![Zusammenfassung „Diagnosetools“](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Diagnosetools: Zusammenfassung")

Das Fenster **Diagnosetools** ist ein gängiges Instrument zum Profilen von Apps. Aber für Releasebuilds können Sie stattdessen auch eine nachträgliche Analyse Ihrer App durchführen. Weitere Informationen zu verschiedenen Herangehensweisen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Informationen zur Unterstützung der Profilerstellungstools für die verschiedenen App-Typen finden Sie unter [Welches Tool soll ich verwenden?](#which-tool-should-i-use).

Zu den Tools, die im Fenster „Diagnosetools“ oder während einer Debugsitzung verfügbar sind, zählen:
- [CPU-Auslastung](../profiling/beginners-guide-to-performance-profiling.md)
- [Speicherauslastung](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools** ). Sie können die [Post-Mortem](#post_mortem)-Tools mit Windows 7 und höher verwenden. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Messen der Leistung in Releasebuilds

Tools im Leistungs-Profiler dienen zur Analyse der **Releasebuilds**. Im Leistungs-Profiler können Sie Diagnoseinformationen sammeln, während die App ausgeführt wird, und anschließend die gesammelten Informationen überprüfen, nachdem die App angehalten wurde (eine Post-Mortem-Analyse).

Öffnen Sie den Leistungs-Profiler durch Wählen von **Debuggen** > **Leistungs-Profiler** (oder drücken Sie **ALT+F2** ).

![Leistungs-Profiler](../profiling/media/prof-tour-performance-profiler.png "Leistungs-Profiler")

Weitere Informationen zur Verwendung des Tools „CPU-Auslastung“ oder „Speicherauslastung“ im Leistungs-Profiler im Vergleich zu den in den Debugger integrierten Tools finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Im Leistungs-Profiler verfügbare Tools:

- [CPU-Auslastung](../profiling/cpu-usage.md)
- [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md)
- [Speicherauslastung](../profiling/memory-usage-without-debugging2.md)
- [.NET Async-Tool](../profiling/analyze-async.md)
- [Datenbanktool](../profiling/analyze-database.md)
- [GPU-Nutzung](../profiling/gpu-usage.md)

Informationen zur Unterstützung der Profilerstellungstools für die verschiedenen App-Typen finden Sie unter [Welches Tool soll ich verwenden?](#which-tool-should-i-use).

In einigen Szenarien können Sie im Fenster [mehrere Profilerstellungstools](../profiling/use-multiple-profiler-tools-simultaneously.md) auswählen. Tools wie z.B. CPU-Auslastung stellen möglicherweise ergänzende Daten bereit, die Sie als Hilfe bei Ihrer Analyse verwenden können. Sie können auch den [Befehlszeilen-Profiler](../profiling/profile-apps-from-command-line.md) verwenden, um Szenarios mit mehreren Profilerstellungstools zu ermöglichen.

## <a name="examine-performance-using-perftips"></a>Untersuchen der Leistung mit PerfTips

In den meisten Fällen besteht die einfachste Methode zum Anzeigen von Leistungsinformationen darin, [PerfTips](../profiling/perftips.md) zu verwenden. Mit PerfTips können Sie Leistungsinformationen anzeigen, während Sie mit Ihrem Code interagieren. Sie können Informationen wie z.B. die Dauer des Ereignisses überprüfen (gemessen daran, wann der Debugger zuletzt angehalten wurde oder wann die App gestartet ist). Wenn Sie beispielsweise die Schritt-für-Schritt-Ausführung des Codes (F10, F11) verwenden, zeigt PerfTips Ihnen die App-Laufzeitdauer vom vorherigen Schritt zum nächsten Schritt an.

![Profilerstellungstour „PerfTips“](../profiling/media/prof-tour-perf-tips.png "Profilerstellungstour „PerfTips“")

Sie können PerfTips verwenden, um zu untersuchen, wie lange die Ausführung eines Codeblocks oder einer einzelnen Funktion dauert.

PerfTips zeigt dieselben Ereignisse an, die auch in der Ansicht **Ereignisse** der Diagnosetools angezeigt werden. In der Ansicht **Ereignisse** können Sie verschiedene Ereignisse anzeigen, die beim Debuggen auftreten, z. B. das Festlegen eines Breakpoints oder einer Schritt-für-Schritt-Codeausführung.

![Ansicht „Ereignisse“ in den Diagnosetools](../profiling/media/prof-tour-events.png "Diagnosetools: Ansicht „Ereignisse“")

 > [!NOTE]
 > Wenn Sie über Visual Studio Enterprise verfügen, sehen Sie auch [IntelliTrace-Ereignisse](../debugger/intellitrace.md) auf dieser Registerkarte.

## <a name="analyze-cpu-usage"></a>Analysieren der CPU-Auslastung

Mit dem CPU-Auslastungstool können Sie die Analyse der Leistung Ihrer App starten. So erfahren Sie mehr über die CPU-Ressourcen, die Ihre App in Anspruch nimmt. Sie können das [in den Debugger integrierte CPU-Auslastungstool](../profiling/beginners-guide-to-performance-profiling.md) oder das [Post-Mortem-CPU-Auslastungstool](../profiling/cpu-usage.md) verwenden.

Wenn Sie das in den Debugger integrierte CPU-Auslastungstool verwenden, öffnen Sie das Fenster „Diagnosetool“ (wenn es geschlossen ist, wählen Sie **Debuggen/Fenster/Diagnosetools anzeigen** ). Öffnen Sie beim Debuggen die Ansicht **Zusammenfassung** , und wählen Sie **CPU-Profilerstellung aufzeichnen** aus.

![Aktivieren der CPU-Auslastung in den Diagnosetools](../profiling/media/prof-tour-enable-cpu-profiling.png "Diagnosetools: CPU-Auslastung aktivieren")

Eine Möglichkeit, das Tool einzusetzen, ist das Festlegen zweier Haltepunkte im Code, einen am Anfang und einen am Ende der Funktion, oder in dem Codebereich, den Sie analysieren möchten. Überprüfen Sie die Profilerstellungsdaten, wenn Sie beim zweiten Haltepunkt angehalten werden.

Die Ansicht **CPU-Auslastung** zeigt eine Liste der Funktionen, geordnet nach den am längsten ausgeführten, mit der längsten Funktion oben. Dies kann helfen, Sie zu Funktionen zu führen, in denen Leistungsengpässe auftauchen.

![Ansicht „CPU-Auslastung“ in den Diagnosetools](../profiling/media/prof-tour-cpu-usage.png "Diagnosetools: CPU-Auslastung")

Doppelklicken Sie auf eine Funktion, an der Sie interessiert sind. Ihnen wird eine detailliertere „Schmetterlingsansicht“ aus drei Bereichen angezeigt. Die ausgewählte Funktion befindet sich in der Mitte des Fensters, die aufrufende Funktion auf der linken Seite und die aufgerufenen Funktionen auf der rechten Seite. Unter **Funktionsrumpf** wird die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. Diese Daten können bei der Bewertung helfen, ob die Funktion selbst ein Leistungsengpass ist.

![Aufrufer-/Aufgerufener-Ansicht „Schmetterling“ in den Diagnosetools](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Diagnosetools: Aufrufer-/Aufgerufener-Ansicht")

## <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung

Im Fenster **Diagnosetools** können Sie auch das Tool **Speicherauslastung** verwenden, um die Arbeitsspeicherauslastung in Ihrer App auszuwerten. Beispielsweise können Sie die Anzahl und Größe der Objekte auf dem Heap anzeigen. Sie können das [in den Debugger integrierte Speicherauslastungstool](../profiling/memory-usage.md) oder das [Post-Mortem-Speicherauslastungstool](../profiling/memory-usage-without-debugging2.md) im Leistungs-Profiler verwenden.

.NET-Entwickler können zwischen dem [.NET-Tool für Objektzuordnungen](../profiling/dotnet-alloc-tool.md) und dem Tool zur [Speicherauslastung](../profiling/memory-usage.md) auswählen.

- Das Tool für **.NET-Objektzuordnungen** unterstützt Sie dabei, Zuteilungsmuster und Anomalien in Ihrem .NET-Code zu entdecken, und es unterstützt Sie beim Identifizieren häufiger Probleme mit der Garbage Collection. Dieses Tool wird nur zur Nachbereitung ausgeführt. Sie können dieses Tool auf lokalen Computern oder Remotecomputern ausführen.
- Das Tool für **Arbeitsspeicherauslastung** ist hilfreich für das Identifizieren von Arbeitsspeicherverlusten, die bei .NET-Apps nicht allzu häufig auftreten. Wenn Sie Debuggerfeatures für das Überprüfen des Arbeitsspeichers verwenden müssen, z. B. für das schrittweise Ausführen von Code, wird das [im Debugger integrierte Tool für die Arbeitsspeicherauslastung](../profiling/beginners-guide-to-performance-profiling.md) empfohlen.

Sie müssen mindestens eine Arbeitsspeichermomentaufnahme erfassen, um die Arbeitsspeicherauslastung mit dem **Speicherauslastungstool** zu analysieren. Häufig ist es zum Analysieren von Arbeitsspeicher am Besten, wenn man zwei Momentaufnahmen macht, die erste direkt vor einem vermuteten Arbeitsspeicherproblem und die zweite Momentaufnahme direkt nach dem Auftreten eines vermuteten Arbeitsspeicherproblems. Anschließend können Sie einen Vergleich der zwei Momentaufnahmen anzeigen und sehen, was genau sich geändert hat. In der folgenden Abbildung wird gezeigt, wie eine Momentaufnahme mit dem in den Debugger integrierten Tool erstellt wird.

![Erstellen einer Momentaufnahme in den Diagnosetools](../profiling/media/prof-tour-take-snapshots.gif "Diagnosetools: Momentaufnahmen erstellen")

Wenn Sie auf einen der Pfeillinks klicken, erhalten Sie eine Differenzansicht des Heaps (ein roter Pfeil NACH OBEN für ![Memory Usage Increase](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zunahme der Speicherauslastung") (Zunahme der Speicherauslastung) zeigt eine zunehmende Objektanzahl (links) oder eine höhere Heapgröße (rechts)). Wenn Sie den richtigen Link klicken, erhalten Sie eine differenzielle Heapansicht, sortiert nach Objekten, die in der Heapgröße am meisten erhöht wurden. Dadurch können Sie Speicherprobleme ermitteln. Zum Beispiel wurden in der folgenden Abbildung die Bytes mithilfe des `ClassHandlersStore`-Objekts in der zweiten Momentaufnahme um 3492 Bytes erhöht.

![Differenzansicht „Heap“ in den Diagnosetools](../profiling/media/prof-tour-mem-usage-diff-heap.png "Diagnosetools: Differenzansicht „Heap“")

Wenn Sie statt in der Ansicht **Speicherauslastung** auf den Link auf der linken Seite klicken, ist die Heapansicht nach der Objektanzahl organisiert. Die Objekte eines bestimmten Typs, der die Zahl am meisten erhöht hat, werden oben angezeigt (sortiert nach der Spalte **Anzahlunterschied** ).

## <a name="analyze-resource-consumption-xaml"></a>Analysieren des Ressourcenverbrauchs (XAML)

In XAML-Apps, z.B. Windows Desktop WPF-Apps und UWP-Apps, können Sie mit der Anwendungszeitachse den Ressourcenverbrauch analysieren. Sie können analysieren, wie viel Zeit Ihre Anwendung zum Vorbereiten von Benutzeroberflächenframes (Layout und Render), von Netzwerk- und Datenträgeranforderungen sowie in Szenarios wie Starten von Anwendungen, Laden von Seiten und Ändern von Fenstergrößen benötigt. Wählen Sie die **Anwendungszeitachse** im Leistungsprofiler aus und anschließend **Starten** , um das Tool zu verwenden. Navigieren Sie in Ihrer App zum Szenario mit einem vermuteten Ressourcenverbrauch-Problem, und wählen Sie anschließend **Auflistung beenden** zum Generieren des Berichts aus.

Geringe Framerates im Diagramm **Visueller Durchsatz** entsprechen möglicherweise visuellen Problemen, die Sie beim Ausführen der App sehen. Auf ähnliche Weise können hohe Zahlen des Diagramms **Auslastung des UI-Thread** Problemen mit der Reaktionsfähigkeit der Benutzeroberfläche entsprechen. Im Bericht können Sie den Zeitraum mit einem vermuteten Leistungsproblem auswählen, und anschließend die detaillierten UI-Threadaktivitäten in der Zeitachsendetailansicht (unten) überprüfen.

![Profilerstellungstool für die Anwendungszeitachse](../profiling/media/prof-tour-application-timeline.gif "Profilerstellungstour für die Anwendungszeitachse")

In der Zeitachsendetailansicht finden Sie Informationen wie den Typ der Aktivität (oder das beteiligte Benutzeroberflächenelement) sowie die Dauer der Aktivität. In der Abbildung benötigt beispielsweise ein **Layout** -Ereignis für ein Grid-Steuerelement 57,53 ms.

Weitere Informationen finden Sie unter [Anwendungszeitachse](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Untersuchen von Anwendungsereignissen

Die generische [Ereignisanzeige](../profiling/events-viewer.md) zeigt die Aktivität Ihrer Anwendung in Form einer Liste von Ereignissen wie Laden von Modulen, Starten von Threads und die Systemkonfiguration an. Dadurch können Sie die Leistung Ihrer Anwendung direkt im Profiler von Visual Studio besser diagnostizieren. Dieses Tool ist im Leistungs-Profiler verfügbar. Öffnen Sie den Leistungs-Profiler durch Wählen von **Debuggen** > **Leistungs-Profiler** (oder drücken Sie **ALT+F2** ).

Das Tool zeigt jedes Ereignis in einer Listenansicht. Spalten enthalten Informationen zu jedem Ereignis, wie z. B. Ereignisname, Zeitstempel und Prozess-ID.

![Überwachung in der Ereignisanzeige](../profiling/media/eventviewertrace.png "Überwachung in der Ereignisanzeige")

## <a name="analyze-asynchronous-code-net"></a>Analysieren von asynchronem Code (.NET)

Mit dem Tool [.NET Async](../profiling/analyze-async.md) können Sie die Leistung von asynchronem Code in Ihrer Anwendung analysieren. Dieses Tool ist im Leistungs-Profiler verfügbar. Öffnen Sie den Leistungs-Profiler durch Wählen von **Debuggen** > **Leistungs-Profiler** (oder drücken Sie **ALT+F2** ).

Das Tool zeigt jeden asynchronen Vorgang in einer Listenansicht. Sie sehen für einen asynchronen Vorgang Informationen wie Startzeit, Endzeit und Gesamtzeit.

![Angehaltenes Tool .NET Async](../profiling/media/async-tool-opened.png "Angehaltenes Tool .NET Async")

## <a name="analyze-database-performance-net-core"></a>Analysieren der Datenbankleistung (.NET Core)

Bei .NET Core-Apps, die mit ADO.NET oder Entity Framework Core arbeiten, können Sie mit dem Tool [Datenbank](../profiling/analyze-database.md) die Datenbankabfragen aufzeichnen, die Ihre Anwendung während einer Diagnosesitzung durchführt. Sie können anschließend Informationen zu einzelnen Abfragen analysieren, um Möglichkeiten zur Verbesserung der Leistung Ihrer App zu finden. Dieses Tool ist im Leistungs-Profiler verfügbar. Öffnen Sie den Leistungs-Profiler durch Wählen von **Debuggen** > **Leistungs-Profiler** (oder drücken Sie **ALT+F2** ).

Das Tool zeigt jede Abfrage in einer Listenansicht. Es werden Informationen wie die Startzeit und Dauer der Abfrage angezeigt.

![Speicherbelegung](./media/db-gotosource.png "Zuordnung")

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Überprüfen der UI-Leistung und Barrierefreiheitsereignisse (UWP)

In Ihren UWP-Apps können Sie die **Analyse der Benutzeroberfläche** im Fenster **Diagnosetools** aktivieren. Das Tool sucht nach gemeinsamen Leistungs- oder Barrierefreiheitsproblemen, und zeigt sie in der Ansicht **Ereignisse** an, während Sie debuggen. Die Ereignisbeschreibungen bieten Informationen zur Problembehebung.

![Anzeigen der Ereignisse der Benutzeroberflächenanalyse in den Diagnosetools](../profiling/media/prof-tour-ui-analysis.png "Diagnosetools: Ereignisse der Benutzeroberflächenanalyse anzeigen")

## <a name="analyze-gpu-usage-direct3d"></a>Analysieren der GPU-Nutzung (Direct3D)

In Direct3D-Apps (Direct3D-Komponenten müssen in C++ vorhanden sein) können Sie Aktivitäten auf der GPU überprüfen und Leistungsprobleme analysieren. Weitere Informationen erhalten Sie unter [GPU-Nutzung](./gpu-usage.md). Wählen Sie die **GPU-Nutzung** im Leistungsprofiler und anschließend **Starten** aus, um das Tool zu verwenden. Durchlaufen Sie in Ihrer Anwendung das Szenario, für das Sie ein Profil erstellen wollen, und wählen Sie anschließend **Auflistung beenden** , um einen Bericht zu generieren.

Wenn Sie einen Zeitraum im Diagramm und **Details anzeigen** auswählen, wird eine detaillierte Ansicht wird im unteren Bereich angezeigt. In der Detailansicht können Sie überprüfen, wie viel Aktivität auf jeder CPU und GPU vorhanden ist. Wählen Sie Ereignisse im untersten Bereich aus, um Popups in der Zeitachse aufzurufen. Wählen Sie z.B. das **Vorhanden** -Ereignis aus, um die **Vorhanden** -Aufruf-Popups anzuzeigen. (Die hellgrauen vertikalen VSync-Zeilen informieren darüber, ob für bestimmte **Present** -Aufrufe ein VSync-Ereignis fehlt. Es muss ein **Present** -Aufruf zwischen je zwei VSync-Ereignissen vorliegen, damit die App kontinuierlich 60 FPS erreicht.)

![Profilerstellungstool „GPU-Nutzung“](../profiling/media/prof-tour-gpu-usage.png "Diagramm „GPU-Auslastung“")

Die Diagramme können auch bestimmen, ob es CPU-gebundene oder GPU-gebundene Leistungsengpässe gibt.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analysieren der Leistung (JavaScript UWP)

Für UWP-Apps können Sie das JavaScript-Speichertool und das Tool für die Reaktionsfähigkeit der HTML-Benutzeroberfläche verwenden.

Das JavaScript-Speichertool ähnelt dem für andere App-Typen verfügbaren Speicherauslastungstool. Mit diesem Tool können Sie die Speicherauslastung verstehen und Speicherverluste in Ihrer App finden. Weitere Informationen zu diesem Tool finden Sie unter [JavaScript-Memory](../profiling/javascript-memory.md).

![Profilerstellungstool „JavaScript-Arbeitsspeicher“](../profiling/media/diagjsmemory.png "DiagJSMemory")

Verwenden Sie das Tool für die Reaktionsfähigkeit der HTML-Benutzeroberfläche, um die UI-Reaktionsfähigkeit, die langsame Ladezeit und die langsamen visuellen Updates in UWP-Apps zu diagnostizieren. Der Verbrauch ähnelt dem Anwendungszeitachsen-Tool für andere App-Typen. Weitere Informationen finden Sie unter [HTML-UI-Reaktionsfähigkeit](../profiling/html-ui-responsiveness.md).

![Profilerstellungstool zur Reaktionsfähigkeit der Benutzeroberfläche (HTML)](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analysieren der Netzwerkverwendung (UWP)

In UWP-Apps können Sie mit der `Windows.Web.Http`-API ausgeführte Netzwerkvorgänge analysieren. Dieses Tool hilft Ihnen beim Lösen von Problemen beispielsweise mit dem Zugriff oder der Authentifizierung, einer falschen Cachenutzung oder einer unzureichenden Leistung bei Anzeige und Downloads. Wählen Sie **Netzwerk** im Leistungsprofiler und anschließend **Starten** aus, um das Tool zu verwenden. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Profilerstellungstool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage.png "Diagramm „Netzwerkauslastung“")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen im Tool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage-details.png "Diagramm: „Details zur Netzwerkauslastung“")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analysieren der Leistung (Legacytools)

::: moniker range="vs-2017"
Wenn Sie Funktionen wie z.B. Instrumentation benötigen, die derzeit nicht in der CPU-Nutzung oder in den Speicherauslastungstools vorhanden sind, und Desktop- oder ASP.NET-Apps ausgeführt werden, können Sie für die Profilerstellung den Leistungs-Explorer verwenden. (Wird in UWP-Apps nicht unterstützt.) Weitere Informationen finden Sie unter [Leistungs-Explorer](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
In Visual Studio 2019 wurden der Legacy-Leistungs-Explorer und die zugehörigen Profilerstellungstools wie der Leistungs-Assistent in den Leistungs-Profiler eingefügt, den Sie über **Debuggen** > **Leistungs-Profiler** öffnen können. Welche Diagnosetools im Leistungs-Profiler verfügbar sind, hängt von dem ausgewählten Ziel und dem aktuell geöffneten Startprojekt ab. Das CPU-Auslastungstool stellt die Funktion zur Stichprobenentnahme bereit, die zuvor über den Leistungs-Assistent verfügbar war. Das Instrumentierungstool bietet die instrumentierte Profilerstellungsfunktion (für präzise Aufrufanzahlen und -zeiten), die zuvor im Leistungs-Assistent verfügbar war. Außerdem sind weitere Arbeitsspeichertools im Leistungs-Profiler verfügbar.
::: moniker-end

![Tool „Leistungs-Explorer“](../profiling/media/prof-tour-performance-explorer.png "Leistungs-Explorer")

## <a name="which-tool-should-i-use"></a>Welches Tool soll ich verwenden?

Hier sehen Sie eine Tabelle, in der die verschiedenen Tools aufgelistet sind, die Visual Studio anbietet sowie die verschiedenen Projekttypen, die Sie mit diesen verwenden können:

::: moniker range=">=vs-2019"
|Leistungstool|Windows-Desktop|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[PerfTips](../profiling/perftips.md)|ja|ja|ja|
|[CPU-Auslastung](../profiling/beginners-guide-to-performance-profiling.md)|ja|ja|ja|
|[Speicherauslastung](../profiling/memory-usage.md)|ja|ja|ja|
|[.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md)|Ja (Nur .NET)|ja|ja|
|[GPU-Nutzung](./gpu-usage.md)|ja|ja|nein|
|[Anwendungszeitachse](../profiling/application-timeline.md)|ja (XAML)|ja|nein|
|[Ereignisanzeige](../profiling/events-viewer.md)|ja|ja|ja|
|[.NET Async](../profiling/analyze-async.md)|Ja (Nur .NET)|ja|ja|
|[Datenbank](../profiling/analyze-database.md)|Ja (nur .NET Core)|Nein|Ja (nur ASP.NET Core)|
|[Leistungs-Explorer](#analyze-performance-legacy-tools)|Nein|nein|Nein|
|[IntelliTrace](../debugger/intellitrace.md)|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Leistungstool|Windows-Desktop|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU-Auslastung](../profiling/beginners-guide-to-performance-profiling.md)|ja|Ja|ja|
|[Speicherauslastung](../profiling/memory-usage.md)|ja|ja|ja|
|[GPU-Nutzung](./gpu-usage.md)|ja|ja|nein|
|[Anwendungszeitachse](../profiling/application-timeline.md)|ja (XAML)|ja|nein|
|[PerfTips](../profiling/perftips.md)|ja|ja für XAML, nicht für HTML|ja|
|[Leistungs-Explorer](../profiling/performance-explorer.md)|ja|nein|ja|
|[IntelliTrace](../debugger/intellitrace.md)|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|
|[Netzwerkverwendung](../profiling/network-usage.md)|nein|ja|nein|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|Nein|ja für HTML, nicht für XAML|Nein|
|[JavaScript-Speicher](../profiling/javascript-memory.md)|Nein|ja für HTML, nicht für XAML|Nein|
::: moniker-end


## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md)