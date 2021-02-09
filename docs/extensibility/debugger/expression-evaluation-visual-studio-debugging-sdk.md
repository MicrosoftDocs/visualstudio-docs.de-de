---
title: Ausdrucks Auswertung (Visual Studio-debuggingsdk) | Microsoft-Dokumentation
description: Während des Break-Modus wertet die IDE Ausdrücke aus, die Programmvariablen betreffen. Erfahren Sie, wie die Debug-Engine einen Ausdruck analysiert und auswertet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 772d38b328eca1e0afb6ff48a5ad580d01939527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921479"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ausdrucks Auswertung (Visual Studio-debuggingsdk)
Während des Break-Modus muss die IDE einfache Ausdrücke mit mehreren Programmvariablen auswerten. Um die Auswertung durchzuführen, muss die Debug-Engine (de) einen Ausdruck analysieren und auswerten, der in einem der Fenster der IDE eingegeben wurde.

 Ausdrücke werden mit der [IDebugExpressionContext2::P Ardie Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode erstellt und durch die resultierende [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle dargestellt.

 Die **IDebugExpression2** -Schnittstelle wird von de implementiert und ruft die **evalasync** -Methode auf, um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle an die IDE zurückzugeben, um die Ergebnisse der Ausdrucks Auswertung in der IDE anzuzeigen. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine-Struktur zurück, die verwendet wird, um den Wert eines Ausdrucks in einem **Überwachungs** **Fenster oder im Fenster** "lokal" zu platzieren.

 Das Debug-Paket oder der Session Debug Manager (SDM) ruft [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) auf, um eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zu erhalten, die das Ergebnis der Auswertung darstellt. `IDebugProperty2` verfügt über Methoden, die den Namen, den Typ und den Wert des Ausdrucks zurückgeben. Diese Informationen werden in verschiedenen Debuggerfenstern angezeigt.

## <a name="using-expression-evaluation"></a>Verwenden der Ausdrucks Auswertung
 Zum Verwenden der Ausdrucks Auswertung müssen Sie die [IDebugExpressionContext2::P arltext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und alle Methoden der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle implementieren, wie in der folgenden Tabelle gezeigt.

|Methode|Beschreibung|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron aus.|
|[Abbrechen](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucks Auswertung.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron aus.|

 Die synchrone und asynchrone Auswertung erfordert die Implementierung der [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode. Bei der asynchronen Ausdrucks Auswertung ist die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungs Steuerung und Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
