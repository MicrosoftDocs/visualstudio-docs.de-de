---
title: DebugBreak und __debugbreak | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit der DebugBreak-Funktion und der intrinsischen Funktion __debugbreak die Ausführung des Programms so unterbrechen können, als wäre an der betreffenden Stelle ein Haltepunkt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559770"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak und "_debugbreak"
Die Win32-Funktion [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) oder die systeminterne Funktion [__debugbreak](/cpp/intrinsics/debugbreak) kann an einer beliebigen Stelle im Code aufgerufen werden. `DebugBreak` und `__debugbreak` haben dieselben Auswirkungen wie das Festlegen eines Haltepunkts an dieser Stelle.

 Da durch `DebugBreak` eine Systemfunktion aufgerufen wird, müssen Systemdebugsymbole installiert werden, um sicherzustellen, dass nach dem Abbrechen die richtigen Aufruflisteninformationen angezeigt werden. Andernfalls sind die vom Debugger angezeigten Aufruflisteninformationen möglicherweise um einen Rahmen verschoben sind. Wenn Sie `__debugbreak` verwenden, sind keine Symbole erforderlich.

## <a name="see-also"></a>Siehe auch
- [Intrinsische Compilerfunktionen](/cpp/intrinsics/compiler-intrinsics)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
