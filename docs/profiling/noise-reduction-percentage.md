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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 531ff082197ca1f7e63008aeda1c27e083b569de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922427"
---
# <a name="noise-reduction-percentage"></a>Prozentsatz der Rauschunterdrückung
Standardmäßig ist der Wert der Einstellung für den Prozentsatz der Rauschunterdrückung auf 2 festgelegt. In der Aufrufstruktur werden nur Einträge angezeigt, für die der Prozentsatz der inklusiven Zeit größer oder gleich dieser Einstellung ist. Indem Sie diese Einstellung ändern, können Sie die Anzahl der Einträge, die in der Aufrufstruktur angezeigt werden, festlegen. Wenn der Wert z.B. in 10 geändert wird, werden nur Einträge in der Aufrufstruktur angezeigt, deren inklusive Zeit größer oder gleich 10 % sind. Indem Sie den Wert der Einstellung erhöhen, können Sie den Fokus auf Einträge legen, die einen größeren Einfluss auf die Leistung Ihres Prozesses haben.