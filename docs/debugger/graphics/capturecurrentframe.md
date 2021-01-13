---
title: CaptureCurrentFrame | Microsoft-Dokumentation
description: Verwenden Sie die CaptureCurrentFrame-Methode der VsgDbg-Klasse, um den Rest des aktuellen Frames in der Grafikprotokolldatei zu erfassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d86ac7d23fa209560222415dce50f4e5ac508
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727943"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.

## <a name="syntax"></a>Syntax

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Hinweise
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet. Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird. Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.

 Um Frames zu erfassen, müssen Sie die App so vorbereiten, dass Grafikinformationen erfasst und aufgezeichnet werden, d. h., Sie müssen [Init](init.md) über eine Instanz der `VsgDbg`-Klasse aufgerufen haben, bevor Sie `CaptureCurrentFrame` aufrufen.

## <a name="see-also"></a>Siehe auch
- [Init](init.md)
- [BeginCapture](begincapture.md)