---
title: E/A-Zeit (Threadansicht) | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu E-/A-Segmenten. Diese sind Blockierungszeiten zugeordnet, die als E/A kategorisiert sind. Dies heißt, ein Thread wartet, bis ein E-/A-Vorgang abgeschlossen ist.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915ab6aef595fba7e13321d4e23c08bdd2eadaf3
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721631"
---
# <a name="io-time-threads-view"></a>E/A-Zeit (Threadansicht)
Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als E/A kategorisiert sind. Das bedeutet, dass ein Thread darauf wartet, dass ein E/A-Vorgang abgeschlossen wird. Der Thread wurde möglicherweise in einer API oder von einer E/A-bezogenen Kernelwarteursache blockiert, die von der Parallelitätsschnellansicht als E/A erfasst wird. APIs wie `CreateFile()`, `ReadFile()` und `WSARecv()` gehören zu dieser Gruppe.

## <a name="see-also"></a>Siehe auch
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)