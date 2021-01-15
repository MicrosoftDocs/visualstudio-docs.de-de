---
title: Kanäle (Threadansicht) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie mehr über die Threadansicht bei Verwendung von Kanälen in der Parallelitätsschnellansicht von Visual Studio. Sie können Threadkanäle, Datenträgerkanäle, Markerkanäle und GPU-Kanäle anzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a4ed0a82ad7ddb67cacde2a09f595d0c9250710
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148610"
---
# <a name="channels-threads-view"></a>Kanäle (Threadansicht)
Die Parallelitätsschnellansicht zeigt vier Arten von Kanälen an: Threadkanäle, Datenträgerkanäle, Markerkanäle und GPU-Kanäle.

## <a name="thread-channels"></a>Threadkanäle
 In einem Threadkanal wird der Threadzustand nach Farbe für einen einzigen Thread angezeigt. Wenn Sie den Cursor auf dem Kanalnamen ruhen lassen, wird die Startfunktion für den angegebenen Thread angezeigt. Die Parallelitätsschnellansicht erkennt mehrere Arten von Threads. Die am häufigsten verwendeten Arten werden in der folgenden Tabelle angezeigt.

|Thread|Beschreibung|
|-|-|
|Hauptthread|Der Thread, der die App startete.|
|Arbeitsthread|Ein Thread, der durch den Hauptthread der Anwendung erstellt wurde.|
|CLR-Arbeitsthread|Ein Arbeitsthread, der von der Common Language Runtime (CLR) erstellt wurde.|
|Debuggerhilfe|Ein Arbeitsthread, der von Visual Studio Debugger erstellt wurde.|
|ConcRT-Thread|Ein Thread, der von der Microsoft Concurrency Runtime erstellt wurde.|
|GDI-Thread|Ein Thread, der von GDIPlus erstellt wurde.|
|OLE/RPC-Thread|Ein Thread, der als RPC-Arbeitsthread erstellt wurde.|
|RPC-Thread|Ein Thread, der als RPC-Thread erstellt wurde.|
|Winsock-Thread|Ein Thread, der als Winsock-Thread erstellt wurde.|
|Threadpool|Ein Thread, der vom CLR-Threadpool erstellt wurde.|

## <a name="disk-channels"></a>Datenträgerkanäle
 Datenträgerkanäle entsprechen physischen Laufwerken auf dem Computer. Da für jedes physische Laufwerk im System eigene Kanäle für Lese- und Schreibvorgänge vorhanden sind, weist jedes Laufwerk zwei Kanäle auf. Die Datenträgernummern entsprechen Kernelgerätenamen. Ein Datenträgerkanal wird nur angezeigt, wenn Aktivität auf dem Datenträger vorhanden war.

## <a name="marker-channels"></a>Markerkanäle
 Markerkanäle entsprechen Ereignissen, die durch die App und die Bibliotheken, die sie verwenden, generiert werden. Zum Beispiel generieren die Task Parallel Library, die Parallel Patterns Library und C++ AMP Ereignisse, die als Marker angezeigt werden. Jeder Markerkanal ist einer Thread-ID zugeordnet, die neben der Beschreibung des Kanals angezeigt wird. Die ID identifiziert den Thread, der das Ereignis generiert hat. Die Beschreibung des Kanals enthält den Namen des Anbieters der Ereignisablaufverfolgung für Windows (ETW), der die Ereignisse generierte. Wenn der Kanal Ereignisse der [ SDK für die Parallelitätsschnellansicht](../profiling/concurrency-visualizer-sdk.md) anzeigt, wird auch der Reihenname angezeigt.

## <a name="gpu-channels"></a>GPU-Kanäle
 GPU-Kanäle zeigen Informationen zu DirectX 11-Aktivität auf dem System an.  Jede DirectX-Engine, die mit der Grafikkarte verbunden ist, hat einen separaten Kanal.  Die einzelnen Segmente geben die Zeit an, die mit der Verarbeitung eines DMA-Pakets zugebracht wurde.

## <a name="see-also"></a>Siehe auch
- [Threadansicht](../profiling/threads-view-parallel-performance.md)