---
title: Verwenden von Debuggerfenstern beim Debuggen einer im Vordergrund ausgeführten App | Microsoft-Dokumentation
description: Wenn Sie ein Programm debuggen, das im Vordergrund bleiben muss, verwenden Sie Remotedebuggen, um es nicht im Hintergrund zu platzieren.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03a143ee2d04227171895bf2b14dff92545b9952
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155093"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgeführten Programms verwendet?
## <a name="problem-description"></a>Problembeschreibung
 Es liegt ein Problem beim Zeichnen auf dem Bildschirm vor. Um das Problem beobachten zu können, muss das Programm im Vordergrund bleiben; das bedeutet jedoch, dass kein Zugriff auf die Debuggerfenster möglich wäre. Welche Möglichkeiten gibt es?

## <a name="solution"></a>Lösung
 Wenn Sie über einen zweiten Computer verfügen, können Sie das Remotedebuggen verwenden. So können Sie das Zeichnen auf dem Bildschirm auf dem Remotecomputer beobachten und gleichzeitig den Debugger auf dem Host ausführen. Weitere Informationen zum Remotedebuggen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
