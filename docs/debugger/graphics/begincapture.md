---
title: BeginCapture | Microsoft-Dokumentation
description: Verwenden Sie die BeginCapture-Methode der VsgDbg-Klasse, um ein Erfassungsintervall zu starten, das mit EndCapture beendet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874573"
---
# <a name="begincapture"></a>BeginCapture
Startet ein Erfassungsintervall, das mit `EndCapture` endet.

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Hinweise
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.

 Um ein Intervall zu erfassen, müssen Sie die App so vorbereiten, dass Grafikinformationen erfasst und aufgezeichnet werden, d. h., Sie müssen [Init](init.md) über eine Instanz der `VsgDbg`-Klasse aufgerufen haben, bevor Sie `BeginCapture` oder `EndCapture` aufrufen.

## <a name="see-also"></a>Siehe auch
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)