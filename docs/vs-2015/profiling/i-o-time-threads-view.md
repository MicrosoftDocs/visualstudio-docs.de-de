---
title: E/A-Zeit (Threadansicht) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86c14292edcf8f132a14b67e931c5121105a9dc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187442"
---
# <a name="io-time-threads-view"></a>E/A-Zeit (Threadansicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als E/A kategorisiert sind. Das bedeutet, dass ein Thread darauf wartet, dass ein E/A-Vorgang abgeschlossen wird. Der Thread wurde möglicherweise in einer API oder von einer E/A-bezogenen Kernelwarteursache blockiert, die von der Parallelitätsschnellansicht als E/A erfasst wird. APIs wie `CreateFile()`, `ReadFile()` und `WSARecv()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
