---
title: Steuern der Datensammlung | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Datensammlung durch die Profilerstellungstools starten und beenden und wie Sie die Objekte einschränken, für die Profilerstellungsdaten gesammelt werden. Dies ist ein Übersichtsartikel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b846db263c95f20c6ea4cb6a418973830a5dd8ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720929"
---
# <a name="control-data-collection"></a>Steuern der Datensammlung
Mit den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie steuern, wann Profilerstellungsdaten während einer Leistungssitzung gesammelt werden, und die Funktionen angeben, für die ein Profil erstellt wird. Dieser Abschnitt beschreibt, wie Sie über das Fenster des **Leistungs- Explorers** und der **Steuerung der Datensammlung** das Sammeln von Daten starten und beenden und wie Sie die Anzahl der Objekte beschränken, für die Profilerstellungsdaten gesammelt werden sollen.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Starten und Beenden der Profilerstellung:** Sie können für eine Anwendung ein Profil erstellen, sobald diese Anwendung gestartet wird. Außerdem lässt sich ein Profiler an einen Prozess anfügen, der bereits ausgeführt wird. Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung anhalten und fortsetzen. Sie beenden eine Profilerstellungssitzung, indem Sie die Zielanwendung schließen oder den Profiler von einem laufenden Prozess trennen.|-   [Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Vorgehensweise: Anfügen von Leistungstools an laufende Prozesse und Trennen von laufenden Prozessen](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Vorgehensweise: Anhalten und Fortsetzen der Sammlung von Leistungsdaten](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Konfigurieren der instrumentierten Profilerstellung, um die gesammelten Daten einzuschränken:** Mit Leistungssitzungskonfigurationseigenschaften können Sie das Sammeln von Daten in Profilerstellungsausführungen einschränken, in denen die Instrumentationsmethode verwendet wird. Sie können bestimmte DLL-Dateien, Namespaces, Klassen und Funktionen einschließen oder ausschließen. Außerdem können Sie Funktionen ausschließen, die einem von Ihnen angegebenen Größenschwellenwert nicht entsprechen.|-   [Vorgehensweise: Beschränken der Instrumentierung auf bestimmte DLLs](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Vorgehensweise: Einschränken der Instrumentierung auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Vorgehensweise: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Verwandte Abschnitte
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Siehe auch
- [Leistungs-Explorer](../profiling/performance-explorer.md)
