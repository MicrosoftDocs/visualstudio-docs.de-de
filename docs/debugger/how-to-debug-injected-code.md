---
title: Debuggen von eingefügtem Code | Microsoft-Dokumentation
description: 'Es werden zwei Visual Studio-Verfahren zum Anzeigen von eingefügtem Code beschrieben: 1) im Fenster „Disassemblierung“, 2) in einer Quelldatei, die sowohl den eingefügten als auch den Originalcode enthält.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bce49eebf430ccaca9919c74966fb9efd00b09b
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903947"
---
# <a name="how-to-debug-injected-code"></a>Vorgehensweise: Debuggen von eingefügtem Code

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Die Verwendung von Attributen kann die C++-Programmierung erheblich vereinfachen. Weitere Informationen finden Sie unter [Konzepte](/cpp/windows/attributed-programming-concepts). Einige Attribute werden direkt vom Compiler interpretiert. Andere Attribute fügen Code in den Programmquellcode ein, der anschließend vom Compiler kompiliert wird. Dieser eingefügte Code kann die Programmierung vereinfachen, da weniger Code geschrieben werden muss. Manchmal kann die Anwendung jedoch aufgrund eines Fehlers fehlschlagen, der beim Ausführen von eingefügtem Code auftritt. In diesem Fall möchten Sie den eingefügten Code wahrscheinlich überprüfen. Visual Studio bietet zwei Möglichkeiten, eingefügten Code zu überprüfen:

- Sie können den eingefügten Code im Fenster **Disassemblierung** anzeigen.

- Sie können mit [/Fx](/cpp/build/reference/fx-merge-injected-code) eine zusammengeführte Quelldatei erstellen, die sowohl Original- als auch den eingefügten Code enthält.

Im Fenster **Disassemblierung** werden Assemblysprachanweisungen angezeigt, die für den Quellcode sowie für den mittels Attributen eingefügten Code stehen. Darüber hinaus können im Fenster **Disassemblierung** Quellcodeanmerkungen angezeigt werden.

## <a name="to-turn-on-source-annotation"></a>So aktivieren Sie Quellcodeanmerkungen

- Klicken Sie mit der rechten Maustaste auf das **Disassemblierungsfenster**, und wählen Sie im Kontextmenü **Quellcode anzeigen** aus.

     Wenn Sie wissen, an welcher Stelle sich ein Attribut im Quellcodefenster befindet, können Sie das Kontextmenü verwenden, um den eingefügten Code im **Disassemblierungsfenster** zu suchen.

## <a name="to-view-injected-code"></a>So zeigen Sie eingefügten Code an

1. Der Debugger muss sich im Unterbrechungsmodus befinden.

2. Positionieren Sie den Cursor im Quellcodefenster vor dem Attribut, dessen eingefügter Code angezeigt werden soll.

3. Klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü **Zu Disassemblierung wechseln** aus.

     Wenn sich das Attribut in der Nähe des aktuellen Ausführungspunktes befindet, können Sie das **Disassemblierungsfenster** über das Menü **Debuggen** öffnen.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>So zeigen Sie den Disassemblycode am aktuellen Ausführungspunkt an

1. Der Debugger muss sich im Unterbrechungsmodus befinden.

2. Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Disassemblierung**.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)