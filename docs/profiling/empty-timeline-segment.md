---
title: Leeres Zeitachsensegment | Microsoft-Dokumentation
description: Hier erfahren Sie, warum in Visual Studio Concurrency Visualizer ein Teil einer Zeitachse für eine Kanalart möglicherweise leer ist (über einen weißen Hintergrund verfügt).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4a3265c3b31653d94a686fa8fda12f7699596e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955267"
---
# <a name="empty-timeline-segment"></a>Leeres Zeitachsensegment
In der Nebenläufigkeitsschnellansicht hängt der Grund dafür, dass ein Abschnitt der Zeitachse leer ist (einen weißen Hintergrund aufweist) von der Art des Kanals ab.

- Bei einem CPU-Threadkanal ist der Grund der, dass der Thread in diesem Teil der Zeitachse nicht vorhanden war. Wenn Sie nach Informationen zu dem Thread suchen, finden Sie den Ausführungsabschnitt mithilfe des Zoomsteuerelements oder indem Sie horizontal scrollen.

- Bei einem E/A-Kanal ist der Grund der, dass zu diesem Zeitpunkt für den Zielprozess kein Datenträgerzugriff durchgeführt wurde.

- Bei einem DirectX-Kanal ist der Grund der, dass in diesem Teil der Zeitachse für den Zielprozess keine GPU-Arbeiten durchgeführt wurden.

- Bei einem Markerkanal ist der Grund der, dass keine Marker generiert wurden.

## <a name="see-also"></a>Siehe auch
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
- [Zoomsteuerelement (Threadansicht)](../profiling/zoom-control-threads-view.md)