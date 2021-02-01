---
title: Gleichzeitiges Verwenden mehrerer Profilertools | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über den Leistungs-Profiler, der mit der Absicht entwickelt wurde, mehrere Tools in derselben Sitzung einzusetzen, um Leistungsprobleme besser zu verstehen.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 5a4c4658282f15b6b34562e51be94d9f2be195a8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721176"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Gleichzeitiges Verwenden mehrerer Profilertools

Der Leistungs-Profiler wurde in der Absicht entwickelt, mehrere Tools in derselben Sitzung einzusetzen, um Leistungsprobleme besser zu verstehen. Die meisten Tools im Leistungs-Profiler unterstützen die gleichzeitige Ausführung, wie z. B. die Tools [CPU-Auslastung](../profiling/cpu-usage.md), [.NET Async](../profiling/analyze-async.md) und [Datenbank](../profiling/analyze-database.md). Um Tools gleichzeitig in derselben Diagnosesitzung auszuführen, aktivieren Sie das Kontrollkästchen neben den Tools, und starten Sie dann die Diagnosesitzung.

![Diagnosehub mit allen ausgewählten Tools](../profiling/media/diaghuballtoolsselected.png "Diagnosehub mit allen ausgewählten Tools")

>[!NOTE]
>Bestimmte Tools wie das [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md) können aufgrund ihres hohen Aufwands oder anderer technischer Einschränkungen nicht zusammen mit anderen Tools ausgeführt werden.

## <a name="time-filtering"></a>Zeitfilterung 

Während der Analyse werden Zeitfilterungsvorgänge toolübergreifend angewendet, sodass Sie Informationen in einem Tool nutzen können, um einen Zeitbereich einzugrenzen und Daten in einem anderen Tool zu filtern. Dieses Feature hilft, die Analyse auf bestimmte Punkte in einer Ablaufverfolgung zu lenken und den Zustand der Anwendung zu verstehen.

![Diagnosehub mit Zeitfilterung](../profiling/media/diaghubtimefiltering.png "Diagnosehub mit Zeitfilterung")

## <a name="see-also"></a>Siehe auch

- [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md)
- [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Grundlegendes zu Leistungsauflistungsmethoden](../profiling/understanding-performance-collection-methods-perf-profiler.md)
