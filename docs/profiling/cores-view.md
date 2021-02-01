---
title: Kernansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, welche Informationen von der Kernansicht angegeben werden. Sie kann Sie dabei unterstützen, die Threadaffinität oder Threadpoolverwaltung zu verwenden, um die Cacheleistung zu optimieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b124cc2f609ab7a113fd28f7086172169138d5f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720708"
---
# <a name="cores-view"></a>Kernansicht
Die **Kernansicht** zeigt, wie die Threadausführung den logischen Prozessorkernen zugeordnet wurde (wählen Sie **Analysieren** > **Nebenläufigkeitsschnellansicht** aus, um die Nebenläufigkeitsschnellansicht zu starten). Beim Schreiben von Serveranwendungen kann diese Ansicht nützlich sein: Optimieren Sie die Cacheleistung, indem Sie Threadaffinität oder Threadpoolverwaltung einsetzen. Manchmal kann sich auch die Prüfung von Fällen als hilfreich erweisen, in denen die Verwendung von Threadaffinität das Problem kernübergreifender Migration noch verstärkt hat. Die Kernansicht verfügt über zwei Komponenten: ein Diagramm und eine Legende.

 Das Diagramm bildet logische Kerne auf der y-Achse und die Zeit auf der x-Achse ab. Jeder Thread im Diagramm hat eine eindeutige Farbe, damit Sie seine Bewegung durch Kerne im zeitlichen Verlauf verfolgen können. Sie können die Threads in diesem Diagramm filtern, indem Sie sie im Legendenbereich auswählen.

 Der Legendenbereich enthält einen Eintrag für jede Farbe im Diagramm. Jeder Eintrag zeigt die Threadfarbe und den Threadnamen, die Anzahl der kernübergreifenden Kontextwechsel, die Gesamtzahl der Kontextwechsel und den Prozentsatz der Kontextwechsel, die durch Kerne verlaufen. Die Legende ist nach der Anzahl der kernübergreifenden Kontextwechsel in absteigender Reihenfolge angeordnet. Sie enthält nur jene Threads, die während des angezeigten Zeitraums ausgeführt wurden.  Die Liste wird aktualisiert, wenn Sie zoomen oder schwenken.

## <a name="see-also"></a>Siehe auch
- [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)
- [Auslastungsansicht](../profiling/utilization-view.md)
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)