---
title: Grundlagen zu Leistungssammlungsmethoden des Profilers
description: Hier erfahren Sie mehr über die Datensammlungsmethoden, die von Tools im Visual Studio Leistungs-Profiler verwendet werden.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f9128700f6ad54f3d92108d92e25e13b9ee4266c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921860"
---
# <a name="understand-profiler-performance-collection-methods"></a>Grundlagen zu Leistungssammlungsmethoden des Profilers

In diesem Dokument werden die Datenerfassungsmethoden beschrieben, die von Tools im Visual Studio-Leistungsprofiler verwendet werden. 

## <a name="sampling"></a>Sampling

Bei Samplingmethoden für die Profilerstellung werden statistische Daten zu den Aufgaben erfasst, die während einer Profilerstellung von einer Anwendung ausgeführt wurden. Die Datenerfassung erfolgt durch das Sammeln von Informationen zur Anwendung in einem regelmäßigen Intervall oder mit einer Samplingfrequenz, z. B. jede Millisekunde. Anschließend werden diese Daten analysiert, um ein Modell des Zeitaufwands in der Anwendung zu erstellen. Die Samplingmethode ist schlank und wirkt sich kaum auf die Ausführung der Anwendung aus, für die ein Profil erstellt wird. Zu den Tools im Leistungs-Profiler, die die Samplingmethode verwenden, gehört das Tool [CPU-Auslastung](../profiling/cpu-usage.md).

## <a name="instrumentation"></a>Instrumentierung

Bei der Profilerstellung mit Instrumentierung werden detaillierte Informationen zu den Aufgaben gesammelt, die während einer Profilerstellung von einer Anwendung ausgeführt wurden. Die Datenerfassung erfolgt durch Tools, die entweder Code in eine Binärdatei einfügen, der Zeitinformationen erfasst, oder durch die Verwendung von Rückrufhooks, um während der Ausführung einer Anwendung exakte Informationen über die Zeit und Anzahl der Aufrufe zu erfassen und auszugeben. Im Vergleich zu Ansätzen, die auf Sampling basieren, hat die Instrumentierungsmethode einen hohen Aufwand. Zu den Tools im Leistungs-Profiler, die die Instrumentierung verwenden, gehört das Tool [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md).