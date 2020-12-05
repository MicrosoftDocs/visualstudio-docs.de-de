---
title: Schnittstellen für die Schlüssel Ausdrucks Auswertung | Microsoft-Dokumentation
description: Informieren Sie sich über die Schnittstellen, mit denen Sie sich vertraut machen sollten, wenn Sie eine Ausdrucks Auswertung zusammen mit dem Auswertungs Kontext schreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5693ebee96428b343da2bb14202ffef06fd6dd81
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606683"
---
# <a name="key-expression-evaluator-interfaces"></a>Schnittstellen für die Schlüssel Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn Sie eine Ausdrucks Auswertung (EE) zusammen mit dem Auswertungs Kontext schreiben, sollten Sie mit den folgenden Schnittstellen vertraut sein.

## <a name="interface-descriptions"></a>Schnittstellenbeschreibungen

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Verfügt über eine einzelne Methode, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), mit der eine Datenstruktur abgerufen wird, die den aktuellen Ausführungs Punkt darstellt. Diese Datenstruktur ist eines der drei Argumente, die die Debug-Engine (de) an die [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) -Methode übergibt, um einen Ausdruck auszuwerten. Diese Schnittstelle wird in der Regel vom Symbol Anbieter implementiert.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Verfügt über die [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode, mit der der Speicherbereich abgerufen wird, der den aktuellen Wert eines Symbols enthält. Gibt sowohl die enthaltende Methode, die durch ein [idebugobject](../../extensibility/debugger/reference/idebugobject.md) -Objekt dargestellt wird, als auch das Symbol selbst, das durch ein [idebugfield](../../extensibility/debugger/reference/idebugfield.md) -Objekt dargestellt wird, `IDebugBinder::Bind` den Wert des Symbols zurück. `IDebugBinder` wird normalerweise von der de implementiert.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Stellt einen einfachen Datentyp dar. Verwenden Sie für komplexere Typen, z. b. Arrays und Methoden, die abgeleiteten [idebugarrayfield](../../extensibility/debugger/reference/idebugarrayfield.md) -bzw. [idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) -Schnittstellen. [Idebugcontainerfield](../../extensibility/debugger/reference/idebugcontainerfield.md) ist eine weitere wichtige abgeleitete Schnittstelle, die Symbole mit anderen Symbolen darstellt, wie z. b. Methoden oder Klassen. Die `IDebugField` -Schnittstelle (und deren Ableitungen) wird in der Regel vom Symbol Anbieter implementiert.

     Ein `IDebugField` -Objekt kann verwendet werden, um den Namen und den Typ eines Symbols zu suchen, und kann mit einem [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) -Objekt verwendet werden, um seinen Wert zu ermitteln.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Stellt die tatsächlichen Bits des Lauf Zeit Werts eines Symbols dar. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) nimmt ein [idebugfield](../../extensibility/debugger/reference/idebugfield.md) -Objekt an, das ein Symbol darstellt, und gibt ein [idebugobject](../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück. Die [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) -Methode gibt den Wert des Symbols in einem Arbeitsspeicher Puffer zurück. Ein de implementiert diese Schnittstelle normalerweise, um den Wert einer Eigenschaft im Arbeitsspeicher darzustellen.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Diese Schnittstelle stellt die Ausdrucks Auswertung selbst dar. Die Schlüsselmethode ist "Analyse", die eine [idebugparameedexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Schnittstelle [zurückgibt.](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Diese Schnittstelle stellt einen analysierten Ausdruck dar, der für die Auswertung bereit ist. Die Schlüsselmethode ist [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , die ein IDebugProperty2-Objekt zurückgibt, das den Wert und den Typ des Ausdrucks darstellt.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Diese Schnittstelle stellt einen-Wert und den zugehörigen Typ dar und ist das Ergebnis einer Ausdrucks Auswertung.

## <a name="see-also"></a>Weitere Informationen
- [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)
