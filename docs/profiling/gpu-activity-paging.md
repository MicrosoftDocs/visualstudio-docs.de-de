---
title: GPU-Aktivität (Paging) | Microsoft-Dokumentation
description: Sehen Sie sich die Segmente für „GPU Activity (Paging)“ (GPU-Aktivität (Auslagern)) auf der Registerkarte „Threads“ von Concurrency Visualizer an. Diese Segmente stellen Zeiträume dar, in denen die GPU Auslagerungsanforderungen verarbeitet hat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4467d2a885f4076461110fe288b4e80169158ede
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877095"
---
# <a name="gpu-activity-paging"></a>GPU-Aktivität (Paging)
Die Segmente der **GPU-Aktivität (Paging)** in der Registerkarte **Threads** stellen Zeiten dar, zu denen die GPU Paging-Anforderungen verarbeitet hat.  Die Länge eines Segments stellt den Zeitraum dar, in dem die GPU ein DMA-Paging-Paket (direkter Speicherzugriff) verarbeitet hat. In der Regel werden Paging-Pakete mit der Übertragung von Arbeitsspeicher zwischen CPU und GPU zugeordnet.

 Wenn Sie ein Segment des GPU-Paging auswählen, zeigt der Bericht in der Registerkarte **Aktuelle** Informationen über das verarbeitete DMA-Paket an. Dies umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das DMA-Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wird, verbunden wird.

## <a name="see-also"></a>Siehe auch
- [Auslastungsansicht](../profiling/utilization-view.md)