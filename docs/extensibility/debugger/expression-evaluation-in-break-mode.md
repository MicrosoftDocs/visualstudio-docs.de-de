---
title: Ausdrucks Auswertung im Umbruch Modus | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Prozess, der auftritt, wenn sich der Debugger im Break-Modus befindet und die Ausdrucks Auswertung durchführen muss.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 041e499f4c670b5b31530c7fc0ecb74358a8087f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921508"
---
# <a name="expression-evaluation-in-break-mode"></a>Ausdrucks Auswertung im Break-Modus
Im folgenden Abschnitt wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Break-Modus befindet und die Ausdrucks Auswertung durchführen muss.

## <a name="expression-evaluation-process"></a>Ausdrucks Auswertungsprozess
 Im folgenden sind die grundlegenden Schritte zum Auswerten eines Ausdrucks aufgeführt:

1. Der Session Debug Manager (SDM) ruft [IDebugStackFrame2:: getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um eine Ausdrucks Kontext Schnittstelle, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md), zu erhalten.

2. Der SDM ruft dann [IDebugExpressionContext2::P arsec-Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der zu erteilenden Zeichenfolge auf.

3. Wenn "Parametertext" nicht S_OK zurückgibt, wird der Grund für den Fehler zurückgegeben.

     sonst

     Wenn "Parametertext" S_OK zurückgibt, kann die SDM dann entweder " [IDebugExpression2:: evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) " oder " [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) " aufrufen, um einen endgültigen Wert aus dem analysierten Ausdruck abzurufen.

    - Wenn verwendet `IDebugExpression2::EvaluateSync` wird, kommuniziert die angegebene Rückruf Schnittstelle mit dem laufenden Prozess der Auswertung. Der endgültige Wert wird in einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurückgegeben.

    - Wenn verwendet `IDebugExpression2::EvaluateAsync` wird, kommuniziert die angegebene Rückruf Schnittstelle mit dem laufenden Prozess der Auswertung. Wenn die Auswertung fertig ist, sendet evaluateasync eine [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Schnittstelle über den Rückruf. Mit dieser Ereignis Schnittstelle ergibt sich der endgültige Wert mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
