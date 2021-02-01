---
title: Stapelblockierung wird aufgehoben | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Aufrufliste eines Threads, der die Aufhebung einer Blockierung durchgeführt hat. Diese wird nach Aufhebung der Blockierung durch einen anderen Threads im aktuellen Prozess auf der Registerkarte angezeigt.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.unblockedby
helpviewer_keywords:
- Concurrency Visualizer, Unblocking Stack
ms.assetid: 1a4dfd9a-e7e2-4aa3-93e2-4f12c7b0970f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30b4da23ef89f8bdde61bbf1eebb63bb4d239b7b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722359"
---
# <a name="unblock-stack"></a>Aufheben der Stapelblockierung
Wenn das derzeit ausgewählte Threadelement ein blockiertes Segment darstellt, das später mit der Ausführung begonnen hat, nachdem seine Blockierung von einem anderen Thread im aktuellen Prozess aufgehoben wurde, wird die Aufrufliste für den Thread, der die Blockierung aufgehoben hat, auf dieser Registerkarte angezeigt.

## <a name="see-also"></a>Siehe auch
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)