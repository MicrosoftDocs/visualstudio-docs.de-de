---
title: CPU-Auslastungsdiagramm | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das CPU-Auslastungsdiagramm, das den Grad der Auslastung in einer App im Zeitverlauf zeigt. Die Auslastung wird als die Anzahl der jeweils verwendeten logischen Kerne angezeigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b310510a87e450c0d6b83a457cd117267ce0c9b8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719018"
---
# <a name="cpu-utilization-graph"></a>CPU-Auslastungsdiagramm
Das CPU-Auslastungsdiagramm veranschaulicht den Grad der Auslastung in einer App im Zeitverlauf. Die x-Achse stellt die Dauer der Ablaufverfolgung dar, die y-Achse die Anzahl der logischen Kerne im System. Im Diagramm ist nicht ersichtlich, welcher bestimmte Kern zu einem bestimmten Zeitpunkt aktiv ist. Wenn beispielsweise zwei Kerne mit einer Kapazität von 50% während eines bestimmten Zeitraums aktiv sind, zeigt diese Ansicht einen logischen Kern, der verwendet wird.

## <a name="cpu-utilization-graph-colors"></a>Farben des CPU-Auslastungsdiagramms

- Grün zeigt die Auslastung der logischen Kerne im System durch den aktuellen Prozess an.

- Hellgrau zeigt die Auslastung der logischen Kerne durch andere Prozesse im System an. Ein hoher hellgrauer Anteil im CPU-Diagramm zeigt, dass das System durch andere Prozesse stark ausgelastet ist und dass diese wahrscheinlich Vorrang vor Ihrem Prozess haben. Zur Verringerung der Auslastung logischer Kerne durch andere Prozesse reduzieren Sie die Anzahl der im System ausgeführten Prozesse.

- Dunkelgrau gibt die Auslastung der logischen Kerne durch den Systemprozess an. Dies können Sie nicht direkt steuern. Allerdings sollten Sie wissen, wann es dazu kommt, da die Verfügbarkeit logischer Kerne für den Prozess beeinträchtigt werden kann.

- Weiß gibt die Verfügbarkeit nicht verwendeter logischer Kerne im System an. Solche Kerne sind für den Prozess verfügbar, wenn Sie mehr Möglichkeiten für eine parallele Nutzung finden.

## <a name="see-also"></a>Siehe auch
- [Auslastungsansicht](../profiling/utilization-view.md)
- [Durchschnittliche CPU-Auslastung](../profiling/average-cpu-utilization.md)