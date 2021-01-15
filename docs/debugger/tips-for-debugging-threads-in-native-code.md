---
title: Tipps zum Debuggen von Threads in nativem Code | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Tipps zum Debuggen von Threads in nativem Code, wenn Sie Multithreadanwendungen in Visual Studio debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150053"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in systemeigenem Code
Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in systemeigenem Code hilfreich sein können:

- Sie können den Inhalt des Threadinformationsblocks anzeigen, indem Sie `@TIB` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.

- Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie `@Err` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.

- Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)