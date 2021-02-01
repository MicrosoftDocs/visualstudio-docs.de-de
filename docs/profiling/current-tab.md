---
title: Registerkarte „Aktuell“ | Microsoft-Dokumentation
description: Klicken Sie in der Ansicht „Threads“ auf die Registerkarte „Aktuell“, um eine Aufrufliste für ein CPU-Threadsegment oder ein Blockierungssegment anzuzeigen. Sie erhalten außerdem Informationen zu DirectX-Segmenten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65261d6304ead5ade7c28f40495fa68afb0c2171
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686215"
---
# <a name="current-tab"></a>Registerkarte „Aktuell“
Bei der Auswahl eines CPU-Threadsegments wird durch Klicken auf die Registerkarte **Aktuell** eine Aufrufliste (sofern vorhanden) angezeigt, die dem aktuellen Auswahlpunkt auf der Zeitachse am ehesten entspricht.  In diesem Fall wird der Auswahlpunkt durch einen schwarzen Pfeil oder ein Caretzeichen oberhalb der Zeitachse dargestellt. Wenn ein Blockierungssegment ausgewählt wird, wird das Caretzeichen nicht angezeigt, weil keine Ausführung stattgefunden hat. Das Segment wird aber dennoch hervorgehoben, und eine Aufrufliste wird angezeigt.

 Auf der Registerkarte **Aktuell** werden zudem Informationen zu DirectX-Aktivitätssegmenten, Marker und E/A-Zugriff angezeigt.  Für DirectX-Aktivitätssegmente werden Informationen zur Verarbeitung von DMA-Paketen durch die Hardwarewarteschlange angezeigt.  Für Marker werden Informationen zur Beschreibung sowie zum Markertyp angezeigt.  Für den E/A-Zugriff werden Informationen zu Datei und Anzahl der gelesenen oder geschriebenen Bytes angezeigt.

## <a name="see-also"></a>Siehe auch
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)