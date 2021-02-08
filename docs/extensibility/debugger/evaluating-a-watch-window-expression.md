---
title: Auswerten eines Überwachungs Fenster Ausdrucks | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio die Debug-Engine aufruft, um den aktuellen Wert der einzelnen Ausdrücke in der Überwachungsliste zu ermitteln, wenn die Ausführung angehalten wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34367b836e766754ce5e274698eb4f5a5d407760
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840612"
---
# <a name="evaluate-a-watch-window-expression"></a>Auswerten eines Überwachungs Fenster Ausdrucks
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn die Ausführung angehalten wird, ruft Visual Studio die Debug-Engine (de) auf, um den aktuellen Wert der einzelnen Ausdrücke in der Überwachungsliste zu ermitteln. Das-Element wertet jeden Ausdruck mithilfe einer Ausdrucks Auswertung (EE) aus, und Visual Studio zeigt den Wert im Fenster über **Wachen** an.

 Im folgenden finden Sie eine Übersicht über die Auswertung eines Überwachungslisten Ausdrucks:

1. Visual Studio Ruft den [getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) von de auf, um einen Ausdrucks Kontext zu erhalten, der zum Auswerten von Ausdrücken verwendet werden kann.

2. Für jeden Ausdruck in der Überwachungsliste ruft Visual Studio " [paramesetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " auf, um den Ausdrucks Text in einen analysierten Ausdruck zu konvertieren.

3. `IDebugExpressionContext2::ParseText` Ruft [die](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Analyse auf, um die tatsächliche Verarbeitung des Texts und das Ausgeben eines [idebugparamesedexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekts durchzuführen.

4. `IDebugExpressionContext2::ParseText` erstellt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt und fügt `IDebugParsedExpression` es in das-Objekt ein. Dieses I- `DebugExpression2` Objekt wird dann an Visual Studio zurückgegeben.

5. Visual Studio ruft [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) auf, um den analysierten Ausdruck auszuwerten.

6. `IDebugExpression2::EvaluateSync` übergibt den-Befehl an [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , um die tatsächliche Auswertung durchzuführen, und erzeugt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das an Visual Studio zurückgegeben wird.

7. Visual Studio ruft [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) auf, um den Wert des Ausdrucks zu erhalten, der dann in der Überwachungsliste angezeigt wird.

## <a name="parse-then-evaluate"></a>Dann analysieren und auswerten
 Da das Analysieren eines komplexen Ausdrucks wesentlich länger dauern kann als die Auswertung, wird der Prozess der Auswertung eines Ausdrucks in zwei Schritte unterteilt: 1) analysieren des Ausdrucks und 2) auswerten des analysierten Ausdrucks. Auf diese Weise kann die Auswertung mehrmals erfolgen, aber der Ausdruck muss nur einmal analysiert werden. Der zwischenformatierte Ausdruck wird von der EE in einem [idebugparameterdexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt zurückgegeben, das wiederum gekapselt und von der de als [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zurückgegeben wird. Das- `IDebugExpression` Objekt setzt alle Auswertungen für das- `IDebugParsedExpression` Objekt aus.

> [!NOTE]
> Es ist nicht erforderlich, dass ein EE diesen zweistufigen Prozess befolgt, auch wenn Visual Studio dies annimmt. der EE kann im gleichen Schritt analysieren und auswerten, wenn [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) aufgerufen wird (z. b. wie das Beispiel mycee funktioniert). Wenn Ihre Sprache komplexe Ausdrücke bilden kann, empfiehlt es sich, den Analyseschritt vom Evaluierungs Schritt zu trennen. Dies kann die Leistung im Visual Studio-Debugger erhöhen, wenn viele Überwachungs Ausdrücke angezeigt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispiel Implementierung der Ausdrucks Auswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Verwendet das mycee-Beispiel, um den Prozess der Ausdrucks Auswertung schrittweise zu durchlaufen.

 [Auswerten eines Überwachungs Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md) Erläutert, was nach einer erfolgreichen Ausdrucks Analyse geschieht.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Auswertungs Kontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die beim Aufrufen der Ausdrucks Auswertung (EE) durch die Debug-Engine (de) übermittelt werden.

## <a name="see-also"></a>Weitere Informationen
 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
