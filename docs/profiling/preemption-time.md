---
title: Zeit für die vorzeitige Entfernung | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Zeit für die vorzeitige Entfernung. Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Zeit für die vorzeitige Entfernung kategorisiert wird.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a102b11fdc7608b94b97105b061e28860f41a9a1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719512"
---
# <a name="preemption-time"></a>Zeit für die vorzeitige Entfernung
Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Speicherverwaltungszeit kategorisiert ist. Diese Kategorie impliziert, dass ein Thread aus einem der folgenden Gründe deaktiviert wird:

- Der Planer hat ihn durch einen Thread mit höherer Priorität ersetzt

- Das Ausführungsquantum des Threads ist abgelaufen, und andere Threads konnten ausgeführt werden

  Gleichzeitig wurde ein Thread aufgrund einer Kernelwarteursache blockiert, die die Parallelitätsschnellansicht als vorzeitige Entfernung erfasst. Die vorzeitige Entfernung der Segmente beginnt, wenn ein Thread aus einem logischen Kern übertragen wird, und endet, wenn der Thread mit der Ausführung fortfährt.

  Die QuickInfo für ein vorzeitig entferntes Segment zeigt den Namen des Prozesses oder Threads an, durch die die vorzeitige Entfernung ausgelöst wurde. Dies impliziert allerdings nicht, dass der Prozess oder der Thread, der den Vorgang übernommen hat, auch wirklich während der vorzeitigen Entfernung ausgeführt wurde.

## <a name="see-also"></a>Siehe auch
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)