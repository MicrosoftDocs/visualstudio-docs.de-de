---
title: Prozentsatz der Rauschunterdrückung | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Einstellung „Noise Reduction Percentage “ (Prozentsatz für Rauschunterdrückung). Außerdem erfahren Sie, wie Sie die Anzahl von Einträgen steuern können, die in der Aufrufstruktur angezeigt werden.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f5e743210cebfc904c88c8f45e772db9beeda40
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722853"
---
# <a name="noise-reduction-percentage"></a>Prozentsatz der Rauschunterdrückung
Standardmäßig ist der Wert der Einstellung für den Prozentsatz der Rauschunterdrückung auf 2 festgelegt. In der Aufrufstruktur werden nur Einträge angezeigt, für die der Prozentsatz der inklusiven Zeit größer oder gleich dieser Einstellung ist. Indem Sie diese Einstellung ändern, können Sie die Anzahl der Einträge, die in der Aufrufstruktur angezeigt werden, festlegen. Wenn der Wert z.B. in 10 geändert wird, werden nur Einträge in der Aufrufstruktur angezeigt, deren inklusive Zeit größer oder gleich 10 % sind. Indem Sie den Wert der Einstellung erhöhen, können Sie den Fokus auf Einträge legen, die einen größeren Einfluss auf die Leistung Ihres Prozesses haben.