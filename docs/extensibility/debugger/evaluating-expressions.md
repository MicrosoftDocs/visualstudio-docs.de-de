---
title: Auswerten von Ausdrücken | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Auswerten von Ausdrücken, die aus Zeichen folgen erstellt werden, die von den Fenstern "Auto", "Überwachung", "schnell Überwachung" oder direkt
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a9b8db832207eff93e08f123db57b4beef4eb7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840599"
---
# <a name="evaluate-expressions"></a>Auswerten von Ausdrücken
Ausdrücke werden aus Zeichen folgen **erstellt, die von den Fenstern**"Auto", "über **Wachen**", " **schnell Überwachung**" oder " **direkt** " Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und den Typ der Variablen oder des Arguments sowie dessen Wert enthält. Diese Zeichenfolge wird im entsprechenden IDE-Fenster angezeigt.

## <a name="implementation"></a>Implementierung
 Ausdrücke werden ausgewertet, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst wird durch eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle dargestellt, die einen analysierten Ausdruck darstellt, der für die Bindung und Auswertung innerhalb des angegebenen Ausdrucks Auswertungs Kontexts bereit ist. Der Stapel Rahmen bestimmt den Ausdrucks Auswertungs Kontext, den die Debug-Engine (de) bereitstellt, indem die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle implementiert wird.

 Bei einer Benutzer Zeichenfolge und einer [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle kann eine Debug-Engine (de) eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle abrufen, indem Sie die Benutzer Zeichenfolge an die [IDebugExpressionContext2::P Arset Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode übergibt. Die IDebugExpression2-Schnittstelle, die zurückgegeben wird, enthält den analysierten Ausdruck, der zur Auswertung bereit ist.

 Mit der- `IDebugExpression2` Schnittstelle kann der de den Wert des Ausdrucks durch synchrone oder asynchrone Ausdrucks Auswertung mithilfe von [IDebugExpression2:: evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)erhalten. Dieser Wert wird zusammen mit dem Namen und dem Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet. Der Wert, der Name und der Typ werden durch eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle dargestellt.

 Zum Aktivieren der Ausdrucks Auswertung muss ein de die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstellen implementieren. Sowohl die synchrone als auch die asynchrone Auswertung erfordert die Implementierung der [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode.

## <a name="see-also"></a>Weitere Informationen
- [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)
- [Ausdrucks Auswertungs Kontext](../../extensibility/debugger/expression-evaluation-context.md)
- [Debuggen von Tasks](../../extensibility/debugger/debugging-tasks.md)
