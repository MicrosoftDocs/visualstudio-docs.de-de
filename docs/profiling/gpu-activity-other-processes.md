---
title: GPU-Aktivität (andere Prozesse) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Segmente für „GPU Activity (Other Processes)“ (GPU-Aktivität (andere Prozesse)) in der Ansicht „Threads“ von Concurrency Visualizer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ecb1587545120aef8e18ce847d5e957f3e3cdd
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801320"
---
# <a name="gpu-activity-other-processes"></a>GPU-Aktivität (andere Prozesse)
Die Segmente der **GPU-Aktivität (andere Prozesse)** in der Threads-Ansicht von Concurrency Visualizer stellen Zeiten dar, in denen die GPU Anforderungen im Auftrag von anderen Prozessen im System verarbeitet hat. Diese Anforderungen werden an die GPU als DMA-Pakete (direkter Speicherzugriff) gesendet.  Die Länge eines Segments stellt die Zeitspanne dar, in der das Paket von der GPU verarbeitet wurde.

 Wenn Sie diese Segmentart auswählen, zeigt der Bericht in der Registerkarte **Aktuell** Informationen über das verarbeitete Paket an.  Die Information umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wurde, verbunden wird.