---
title: Bildlauf nach oben oder unten im Arbeitsspeicher | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie „Bildlauf nach oben“ oder „Bildlauf nach unten“ im Arbeitsspeicher verwenden, um die Arbeitsspeicherinhalte beim Debuggen in Visual Studio in einem Arbeitsspeicherfenster oder im Fenster „Disassemblierung“ anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fc586603caf18261654e5ec8ee437c0875616a7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148883"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Vorgehensweise: Bildlauf nach oben oder unten im Arbeitsspeicher

Beim Anzeigen des Speicherinhalts im Fenster **Arbeitsspeicher** oder im Fenster **Disassemblierung** können Sie mithilfe der vertikalen Scrollleiste im Speicher nach oben oder unten navigieren.

### <a name="to-page-up-or-down-in-memory"></a>So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch

1. Für einen Bildlauf nach unten (Navigieren zu einer höheren Speicheradresse) klicken Sie auf die vertikale Bildlaufleiste unter dem Bildlauffeld.

2. Für einen Bildlauf nach oben (Navigieren zu einer niedrigeren Speicheradresse) klicken Sie auf die vertikale Scrollleiste über dem Bildlauffeld.

   Beachten Sie auch, dass das Verhalten der vertikalen Bildlaufleiste nicht dem Standardverhalten entspricht. Der Adressbereich eines modernen Computers ist äußerst groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen. Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste. In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.

   In verwalteten Anwendungen ist die Disassembly auf eine Funktion begrenzt, und Sie können einen normalen Bildlauf durchführen.

   Beachten Sie, dass die höheren Adressen am unteren Rand des Fensters angezeigt werden. Wenn Sie eine höhere Adresse anzeigen möchten, müssen Sie nach unten navigieren, nicht nach oben.

#### <a name="to-move-up-or-down-one-instruction"></a>So wechseln Sie um eine Anweisung nach oben oder unten

- Klicken Sie auf den Pfeil am oberen oder unteren Ende der vertikalen Scrollleiste.

## <a name="see-also"></a>Siehe auch
- [Fenster "Arbeitsspeicher"](../debugger/memory-windows.md)
- [How to: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)