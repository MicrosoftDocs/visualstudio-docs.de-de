---
title: EndCapture | Microsoft-Dokumentation
description: Verwenden Sie die EndCapture-Methode der VsgDbg-Klasse, um ein Erfassungsintervall zu beenden, das mit BeginCapture gestartet wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727830"
---
# <a name="endcapture"></a>EndCapture
Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Hinweise
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.

 Um ein Intervall zu erfassen, müssen Sie die App so vorbereiten, dass Grafikinformationen erfasst und aufgezeichnet werden, d. h., Sie müssen [Init](init.md) über eine Instanz der `VsgDbg`-Klasse aufgerufen haben, bevor Sie `BeginCapture` oder `EndCapture` aufrufen.

## <a name="see-also"></a>Siehe auch
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)