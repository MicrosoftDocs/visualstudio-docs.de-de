---
title: Architektur der Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine proprietäre Sprache in das Visual Studio-Debugpaket integrieren, einschließlich der Ausdrucks Auswertung und der Symbol Anbieter/Binder Schnittstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac81d386f0e1104879701faba230d5384259fa25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921413"
---
# <a name="expression-evaluator-architecture"></a>Architektur der Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Das Integrieren einer proprietären Sprache in das Visual Studio-Debugpaket bedeutet, dass Sie die erforderlichen Schnittstellen für die Ausdrucks Auswertung (EE) einrichten und die Schnittstellen des Common Language Run-Time-Symbol Anbieters (SP) und Binder aufzurufen müssen. Die SP-und Binder Objekte sind zusammen mit der aktuellen Ausführungs Adresse der Kontext, in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen erzeugen und nutzen, stellen die Schlüsselkonzepte in der Architektur eines EE dar.

## <a name="overview"></a>Übersicht

### <a name="parse-the-expression"></a>Ausdruck analysieren
 Wenn Sie ein Programm debuggen, werden Ausdrücke aus einer Reihe von Gründen ausgewertet, aber immer dann, wenn das Programm, das gedebuggt wird, an einem Haltepunkt angehalten wurde (entweder ein Haltepunkt, der vom Benutzer platziert wurde, oder der durch eine Ausnahme verursachte). Zu diesem Zeitpunkt erhält Visual Studio einen Stapel Rahmen, der durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle dargestellt wird, von der Debug-Engine (de). In Visual Studio wird dann [getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aufgerufen, um die [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle zu erhalten. Diese Schnittstelle stellt einen Kontext dar, in dem Ausdrücke ausgewertet werden können. " [Parametertext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " ist der Einstiegspunkt des Evaluierungsprozesses. Bis zu diesem Punkt werden alle Schnittstellen von de implementiert.

 Wenn `IDebugExpressionContext2::ParseText` aufgerufen wird, instanziiert der "de" den EE, der der Sprache der Quelldatei zugeordnet ist, in der der Breakpoint aufgetreten ist (der "de" instanziiert ebenfalls die sh an dieser Stelle). Der EE wird durch die [idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) -Schnittstelle dargestellt. Das de-Element [ruft dann](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) die Analyse auf, um den Ausdruck (in Textform) in einen analysierten Ausdruck zu konvertieren, der für die Auswertung bereit ist. Dieser analysierte Ausdruck wird durch die [idebugparameterdexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Schnittstelle dargestellt. Der Ausdruck wird in der Regel analysiert und zu diesem Zeitpunkt nicht ausgewertet.

 Die de erstellt ein Objekt, das die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle implementiert, das- `IDebugParsedExpression` Objekt in das `IDebugExpression2` -Objekt einfügt und das- `IDebugExpression2` Objekt von zurückgibt `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Ausdruck auswerten
 Visual Studio ruft entweder [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den analysierten Ausdruck auszuwerten. Beide Methoden rufen [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) `IDebugExpression2::EvaluateSync` auf (Ruft die-Methode sofort auf, während `IDebugExpression2::EvaluateAsync` die-Methode über einen Hintergrund Thread aufruft), um den analysierten Ausdruck auszuwerten und eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurückzugeben, die den Wert und den Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync` verwendet die angegebene sh, address und Binder, um den analysierten Ausdruck in einen tatsächlichen Wert zu konvertieren, der durch die- `IDebugProperty2` Schnittstelle dargestellt wird.

### <a name="for-example"></a>Beispiel:
 Nachdem ein Haltepunkt in einem laufenden Programm gedrückt wurde, wählt der Benutzer eine Variable im Dialogfeld **schnell Überwachung** aus. In diesem Dialogfeld werden der Name, der Wert und der Typ der Variablen angezeigt. Der Benutzer kann in der Regel den Wert ändern.

 Wenn das Dialogfeld **schnell Überwachung** angezeigt wird, wird der Name der Variablen, die untersucht wird, als Text an "Parametertext" gesendet. [](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Dies gibt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zurück, das den analysierten Ausdruck darstellt, in diesem Fall die-Variable. [Evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird dann aufgerufen, um ein Objekt zu schaffen, `IDebugProperty2` das den Wert und Typ der Variablen sowie den Namen der Variablen darstellt. Diese Informationen werden angezeigt.

 Wenn der Benutzer den Wert der Variablen ändert, wird [setvalueasstring](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) mit dem neuen Wert aufgerufen, der den Wert der Variablen im Arbeitsspeicher ändert, sodass er verwendet wird, wenn das Programm die Ausführung fortsetzt.

 Weitere Informationen zu diesem Prozess der Anzeige der Werte von Variablen finden Sie unter [Anzeigen von lokalen](../../extensibility/debugger/displaying-locals.md) Variablen. Weitere Informationen zur Änderung des Werts einer Variablen finden Sie unter [Ändern des Werts einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) Variablen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Auswertungs Kontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die beim Aufrufen von EE an den EE übermittelt werden.

 [Schnittstellen für die Schlüssel Ausdrucks Auswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Beschreibt die entscheidenden Schnittstellen, die erforderlich sind, wenn ein EE zusammen mit dem Auswertungs Kontext geschrieben wird.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)
- [Ändern des Werts eines lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md)
