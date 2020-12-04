---
title: Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie mehr über Ausdrucks Auswertungs, die die Syntax einer Sprache untersuchen, um Variablen und Ausdrücke zur Laufzeit im Break-Modus zu analysieren und auszuwerten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8223e39eb804684fede50ceb2f7c859e198a272
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560134"
---
# <a name="expression-evaluator"></a>Expression evaluator (Ausdrucksauswertung)
Die Ausdrucks Auswertung (EE) untersuchen die Syntax einer Sprache, um Variablen und Ausdrücke zur Laufzeit zu analysieren und auszuwerten, sodass Sie vom Benutzer angezeigt werden können, wenn sich die IDE im unterbrechen Modus befindet.

## <a name="use-expression-evaluators"></a>Verwenden von Ausdrucks auswergratoren
 Ausdrücke werden [mithilfe der Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) "Methode" wie folgt erstellt:

1. Die Debug-Engine (de) implementiert die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle.

2. Das Debugpaket `IDebugExpressionContext2` Ruft ein Objekt aus einer [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle ab und ruft dann die- `IDebugStackFrame2::ParseText` Methode auf, um ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zu erhalten.

3. Das Debugpaket Ruft die [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) -Methode oder die [evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methode auf, um den Wert des Ausdrucks zu erhalten. `IDebugExpression2::EvaluateAsync` wird im Fenster Befehl/direkt aufgerufen. Alle anderen UI-Komponenten erfordern `IDebugExpression2::EvaluateSync` .

4. Das Ergebnis der Ausdrucks Auswertung ist ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das den Namen, den Typ und den Wert des Ergebnisses der Ausdrucks Auswertung enthält.

   Während der Ausdrucks Auswertung benötigt der EE Informationen von der Symbol Anbieter Komponente. Der Symbol Anbieter liefert die symbolischen Informationen, die zum Identifizieren und verstehen des analysierten Ausdrucks verwendet werden.

   Wenn die asynchrone Ausdrucks Auswertung abgeschlossen ist, wird von der de durch den Sitzungs-Debug-Manager (SDM) ein asynchrones Ereignis gesendet, um die IDE zu benachrichtigen, dass die Ausdrucks Auswertung abgeschlossen ist. Das Ergebnis der Auswertung wird dann vom aufrufswert der-Methode zurückgegeben `IDebugExpression2::EvaluateSync` .

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-engines erwarten mit der Ausdrucks Auswertung mithilfe von CLR-Schnittstellen (Common Language Runtime). Daher muss eine Ausdrucks Auswertung, die mit debuggingmodulen arbeitet, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die CLR unterstützen (eine vollständige Liste aller CLR-Debugschnittstellen finden Sie in debugref.doc, die Teil von ist [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Siehe auch
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
