---
title: Suchen eines Aufruffehlers beim mehrfachen Aufrufen einer Funktion
description: In diesem Artikel wird ein Verfahren zum Festlegen eines Breakpoints für eine Funktion vorgestellt, damit die Unterbrechung nur für den Aufruf auftritt, für den die Funktion fehlschlägt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567450f11572cc998f952117c33992cdba33570d
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149299"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr häufig aufgerufen wird?
## <a name="problem-description"></a>Problembeschreibung
 Das Programm schlägt bei einem Aufruf einer bestimmten Funktion mit dem Namen `CnvtV` fehl. Zuvor hat das Programm die Funktion jedoch mehrere Hundert Male aufgerufen. Wenn ein Positionshaltepunkt für `CnvtV` festgelegt wird, hält das Programm bei jedem Aufruf der Funktion an, was nicht beabsichtigt ist. Da nicht bekannt ist, welche Bedingungen den fehlschlagenden Aufruf verursachen, kann kein bedingter Haltepunkt festgelegt werden. Welche Möglichkeiten gibt es?

## <a name="solution"></a>Lösung
 Mithilfe des Felds **Trefferanzahl** können Sie einen Haltepunkt für die Funktion auf einen hohen Wert festlegen, der niemals erreicht wird. Da Sie davon ausgehen, dass die `CnvtV`-Funktion einige Hundert Male aufgerufen wird, könnten Sie **Trefferanzahl** auf einen Wert von mindestens 1000 festlegen. Führen Sie dann das Programm aus, und warten Sie, bis der Aufruf fehlschlägt. Sobald dies der Fall ist, öffnen Sie das Fenster "Haltepunkte" und überprüfen die Haltepunktliste. Der für `CnvtV` festgelegte Haltepunkt wird, gefolgt von der Trefferanzahl und der Anzahl der noch verbleibenden Iterationen, angezeigt:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Jetzt wissen Sie, dass die Funktion bei Aufruf Nr. 101 fehlgeschlagen ist. Wenn Sie nun den Haltepunkt auf eine Trefferanzahl von 101 zurücksetzen und das Programm erneut ausführen, hält es an dem `CnvtV`-Aufruf an, der zuvor den Fehler verursacht hat.

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Setting Breakpoints (Setzen von Haltepunkten)](/previous-versions/ktf38f66(v=vs.100))
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)