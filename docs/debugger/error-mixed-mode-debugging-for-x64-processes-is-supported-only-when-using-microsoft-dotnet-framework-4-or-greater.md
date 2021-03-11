---
description: Um gemischten nativen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie .NET Framework Version 4.
title: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 31ae6b1c4a80f7d28cdbbdd2c4d944cddf15227d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146950"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
Um gemischten nativen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie .NET Framework Version 4. Das Debuggen von 64-Bit-Prozessen im gemischten Modus mit .NET Framework wird erst ab Version 4 unterstützt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Führen Sie einen der folgenden Schritte aus:

  - Aktualisieren Sie .NET Framework auf Version 4.

  - Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
