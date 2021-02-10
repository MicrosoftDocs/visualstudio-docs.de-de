---
title: Leistungsregeln für die Ressourcenüberwachung | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über Leistungsmeldungen in der Kategorie „Ressourcenüberwachung“, die zusätzliche Daten zur Leistung Ihrer Anwendung bereitstellen.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fc17bd86868a7b3e87c47ec44fd5caabf7a6cfd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950142"
---
# <a name="resource-monitoring-performance-rules"></a>Leistungsregeln für die Ressourcenüberwachung
Über Leistungsmeldungen in der Kategorie „Ressourcenüberwachung“ erhalten Sie zusätzliche Informationen zur Leistung Ihrer Anwendung. Sie können diese Daten verwenden, um Probleme mit der Leistung zu analysieren. Diese Regeln haben einen informativen Charakter und werden bei jeder Profilerstellung angezeigt.

|Regel|Beschreibung|
|-|-|
|[DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|
|[DA0502: Maximale CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der maximale Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|
|[DA0503: Durchschnittliche Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die durchschnittliche Menge an physischem Speicher (in Bytes), der von dem Prozess bei der Profilerstellung belegt wurde. Diese Einheit für den physischen Speicher ist unter der Bezeichnung „Arbeitssatz“ bekannt.|
|[DA0504: Maximale Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|In dieser Meldung wird die maximale Menge an physischem Arbeitsspeicher (in Bytes) angegeben, der von dem Prozess bei der Profilerstellung belegt wurde.|
|[DA0505: Durchschnittswert für „Private Bytes“, das dem Prozess, für den die Profilerstellung ausgeführt wird, zugeordnet ist](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|In dieser Meldung wird die durchschnittliche Menge an virtuellem Arbeitsspeicher in Bytes angegeben, der von dem Prozess bei der Profilerstellung belegt wurde. Diese Einheit für den virtuellen Speicher ist unter der Bezeichnung *private Bytes* bekannt. Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.|
|[DA0506: Höchstwert für „Private Bytes“, der dem Prozess, für den die Profilerstellung ausgeführt wird, zugeordnet ist](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher in privaten Bytes angegeben, der von dem Prozess bei der Profilerstellung belegt wurde.|
