---
title: Ereignisanzeige | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die generische Ereignisanzeige, mit der Sie die Leistung Ihrer App im Visual Studio-Profiler besser diagnostizieren können.
ms.custom: SEO-VS-2020
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 6aef8e72f416923aa647a8b3a412ee701ece18dd
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801409"
---
# <a name="events-viewer"></a>Ereignisanzeige

Die generische Ereignisanzeige zeigt die App-Aktivität anhand einer Liste von Ereignissen wie Laden von Modulen, Starten von Threads und die Systemkonfiguration an. Mit dieser Ansicht können Sie besser diagnostizieren, wie sich Ihre App innerhalb des Visual Studio-Profilers verhält.

## <a name="setup"></a>Setup

1. Öffnen Sie über **ALT+F2** den Leistungs-Profiler in Visual Studio.

1. Aktivieren Sie das Kontrollkästchen **Ereignisanzeige**.

   ![Das aktivierte Kontrollkästchen „Ereignisanzeige“](../profiling/media/eventsviewerselected.png "Das aktivierte Kontrollkästchen „Ereignisanzeige“")

1. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

1. Gehen Sie nach dem Start des Tools das Szenario durch, für das Sie in Ihrer App ein Profil erstellen möchten. Klicken Sie dann auf **Sammlung beenden**, oder schließen Sie Ihre App, um die Daten anzuzeigen.

   ![Fenster mit angezeigter Option „Sammlung beenden“](../profiling/media/stopcollectioneventsviewer.png "Fenster mit angezeigter Option „Sammlung beenden“")

Weitere Informationen zur Optimierung des Tools finden Sie unter [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Erläuterungen zu den Daten

![Eine Überwachung in der Ereignisanzeige](../profiling/media/eventviewertrace.png "Eine Überwachung in der Ereignisanzeige")

|Spaltenname|Beschreibung|
|----------|---------------------|
|Anbietername|Die Ereignisquelle|
|Ereignisname|Das Ereignis, wie von seinem Anbieter angegeben|
|Text|Beschreibung des Anbieters, Name und ID des Ereignisses|
|Zeitstempel (ms)|Zeitpunkt des Ereignisses|
|Anbieter-GUID|Die ID des Ereignisanbieters|
|Ereignis-ID|Die ID des Ereignisses|
|Prozess-ID|Der Prozess, in dem das Ereignis aufgetreten ist (falls bekannt)|
|Prozessname|Der Name des Prozesses, der aktiv ausgeführt wird|
|Thread-ID|Die ID des Threads, in dem das Ereignis aufgetreten ist (falls bekannt)|

Wenn eine Spalte standardmäßig fehlt, klicken Sie mit der rechten Maustaste auf eine der vorhandenen Spaltenüberschriften, und wählen Sie die Spalte aus, die Sie hinzufügen möchten.

![Hinzufügen von Spalten zur Ereignisanzeige](../profiling/media/eventvieweraddcolumns.png "Hinzufügen von Spalten zur Ereignisanzeige")

Wenn Sie ein Ereignis auswählen, wird das Fenster **Zusätzliche Eigenschaften** angezeigt. **Allgemeine Eigenschaften** enthält eine Liste der Eigenschaften, die für ein beliebiges Ereignis angezeigt werden. **Nutzlasteigenschaften** enthält Eigenschaften, die für das Ereignis spezifisch sind. Bei einigen Ereignissen können Sie auch **Stapel** anzeigen.

![Ereignisanzeige mit Stapeln](../profiling/media/eventviewerstacks.png "Ereignisanzeige mit Stapeln")

## <a name="organize-your-data"></a>Organisieren von Daten

Alle Spalten mit Ausnahme von **Text** sind sortierbar.

![Überwachung in der Ereignisanzeige](../profiling/media/eventviewertrace.png "Überwachung in der Ereignisanzeige")

In der Ereignisanzeige werden bis zu 20.000 Ereignisse gleichzeitig angezeigt. Um sich auf die relevanten Ereignisse zu konzentrieren, können Sie die Anzeige der Ereignisse durch Auswählen des Ereignisfilters filtern. Sie können auch erkennen, welcher Prozentsatz der Gesamtanzahl der Ereignisse bei den einzelnen Anbietern aufgetreten ist. Bewegen Sie den Mauszeiger über einen einzelnen Ereignisfilter, um eine QuickInfo aufzurufen, die Folgendes zeigt:

- Ereignisname
- Anbieter
- GUID
- Prozentsatz der Gesamtanzahl der Ereignisse
- Ereignisanzahl

![Der Ereignisfilter in der Ereignisanzeige](../profiling/media/eventviewereventfilter.png "Der Ereignisfilter in der Ereignisanzeige")

Der Anbieterfilter zeigt, welcher Prozentsatz der Gesamtanzahl der Ereignisse bei den einzelnen Anbietern aufgetreten ist. Bewegen Sie den Mauszeiger über einen einzelnen Anbieter, um eine ähnliche QuickInfo mit dem Namen des Anbieters, dem Prozentsatz der Gesamtanzahl der Ereignisse und der Anzahl der Ereignisse anzuzeigen.

![Der Anbieterfilter in der Ereignisanzeige](../profiling/media/eventviewerproviderfilter.png "Der Anbieterfilter in der Ereignisanzeige")
