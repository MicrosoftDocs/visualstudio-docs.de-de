---
title: Auslastungsnavigator | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie mit dem Auslastungsnavigator in Concurrency Visualizer ein Zeitintervall in einer Ablaufverfolgung auswählen können.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d92747bb90cae18a79e81e49689ce8c01b8a9b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917570"
---
# <a name="utilization-navigator"></a>Auslastungsnavigator
Mit dem Auslastungsnavigator können Sie in der Nebenläufigkeitsschnellansicht ein Zeitintervall in einer Ablaufverfolgung auswählen. In der Nebenläufigkeitsschnellansicht wird die Auslastung der CPU-Kerne durch den Zielprozess im Verlauf der Zeit angezeigt. Damit lassen sich CPU-Auslastungsmuster leichter erkennen. Zudem können die Auslastungsdaten mit den Daten in anderen Ansichten verglichen werden. Der Auslastungsnavigator wird in der Nebenläufigkeitsschnellansicht in allen Ansichten im oberen Bereich angezeigt. Der Auslastungsnavigator ist in der folgenden Abbildung dargestellt.

 ![Auslastungsnavigator zeigt ausgewählten Zeitrahmen an](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Der Auslastungsnavigator mit einem ausgewählten Zeitrahmen

 In der Abbildung ist zu sehen, dass das ausgewählte Intervall durch ein rotes Rechteck definiert wird. Dies wird als *Thumb* bezeichnet.

 So können Sie mithilfe des Auslastungsnavigators den angezeigten Zeitbereich bearbeiten:

- Sie können ihn schwenken, indem Sie den Thumb nach links oder rechts ziehen. (Tastatur: Verschieben Sie den Fokus auf den Thumb, und drücken Sie anschließend die Pfeiltaste nach links oder rechts.)

- Sie können die Größe des Zeitintervalls ändern, indem Sie einen der Ziehpunkte ziehen. (Tastatur: Verschieben Sie den Fokus auf einen Ziehpunkt, und drücken Sie anschließend die Pfeiltaste nach rechts oder links.)

  Wenn Sie das Intervall mit einem anderen Zoomsteuerelement der Nebenläufigkeitsschnellansicht ändern, wird die Änderung vom Auslastungsnavigator übernommen.