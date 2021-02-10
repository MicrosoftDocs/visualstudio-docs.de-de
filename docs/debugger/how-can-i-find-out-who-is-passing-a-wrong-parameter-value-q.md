---
title: Ermitteln, woher ein falscher Parameterwert stammt | Microsoft-Dokumentation
Description: Sie können herausfinden, welcher Code die Funktion aufruft und einen falschen Parameterwert übergibt. Erfahren Sie, wie Sie hierfür einen bedingten Haltepunkt verwenden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d159198137c70810bc47cc79caf18ac178aeecd6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912270"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Wie wird festgestellt, woher der falsche Parameterwert stammt?
## <a name="problem-description"></a>Problembeschreibung
 An eine Funktion wird der falsche Parameterwert übergeben. Diese Funktion wird von mehreren Stellen aus aufgerufen. Wie kann festgestellt werden, woher der falsche Wert stammt?

## <a name="solution"></a>Lösung

#### <a name="to-resolve-this-problem"></a>So beheben Sie dieses Problem

1. Legen Sie am Anfang der Funktion einen Positionshaltepunkt fest.

2. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingung** aus.

3. Aktivieren Sie im Dialogfeld **Bedingung für Haltepunkt** das Kontrollkästchen **Bedingung**. Siehe [Erweiterte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Geben Sie einen Ausdruck, z. B. `Var==3`, in das Textfeld ein, wobei `Var` der Name des Parameters ist, der den falschen Wert enthält, und `3` der übergebene falsche Wert.

5. Aktivieren Sie das Optionsfeld **is True** (ist TRUE), und klicken Sie auf die Schaltfläche **OK**.

6. Führen Sie nun das Programm erneut aus. Der Haltepunkt bewirkt, dass das Programm am Funktionsanfang anhält, sobald `Var` den Wert `3` hat.

7. Im Fenster Aufrufliste sehen Sie die aufrufende Funktion und können zu ihrem Quellcode navigieren. Weitere Informationen finden Sie unter [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Breakpoints](/previous-versions/ktf38f66(v=vs.100))
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)