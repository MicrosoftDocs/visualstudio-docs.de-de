---
title: Auswerten von Ausdrücken | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738830"
---
# <a name="evaluate-expressions"></a>Auswerten von Ausdrücken
Ausdrücke werden aus Zeichen folgen **erstellt, die von den Fenstern**"Auto", "über **Wachen**", " **schnell Überwachung**" oder " **direkt** " Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und den Typ der Variablen oder des Arguments sowie dessen Wert enthält. Diese Zeichenfolge wird im entsprechenden IDE-Fenster angezeigt.

## <a name="implementation"></a>Implementierung
 Ausdrücke werden ausgewertet, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst wird durch eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle dargestellt, die einen analysierten Ausdruck darstellt, der für die Bindung und Auswertung innerhalb des angegebenen Ausdrucks Auswertungs Kontexts bereit ist. Der Stapel Rahmen bestimmt den Ausdrucks Auswertungs Kontext, den die Debug-Engine (de) bereitstellt, indem die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle implementiert wird.

 Bei einer Benutzer Zeichenfolge und einer [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle kann eine Debug-Engine (de) eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle abrufen, indem Sie die Benutzer Zeichenfolge an die [IDebugExpressionContext2::P Arset Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode übergibt. Die IDebugExpression2-Schnittstelle, die zurückgegeben wird, enthält den analysierten Ausdruck, der zur Auswertung bereit ist.

 Mit der- `IDebugExpression2` Schnittstelle kann der de den Wert des Ausdrucks durch synchrone oder asynchrone Ausdrucks Auswertung mithilfe von [IDebugExpression2:: evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)erhalten. Dieser Wert wird zusammen mit dem Namen und dem Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet. Der Wert, der Name und der Typ werden durch eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle dargestellt.

 Zum Aktivieren der Ausdrucks Auswertung muss ein de die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstellen implementieren. Sowohl die synchrone als auch die asynchrone Auswertung erfordert die Implementierung der [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode.

## <a name="see-also"></a>Siehe auch
- [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)
- [Ausdrucks Auswertungs Kontext](../../extensibility/debugger/expression-evaluation-context.md)
- [Aufgaben Debuggen](../../extensibility/debugger/debugging-tasks.md)
