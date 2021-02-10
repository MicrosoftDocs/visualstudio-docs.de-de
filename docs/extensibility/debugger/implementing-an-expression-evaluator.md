---
title: Implementieren einer Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Auswerten eines Ausdrucks, der die Debug-Engine, den Symbol Anbieter, das Binder Objekt und die Ausdrucks Auswertung umfasst.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121bd17e2343cfbba509e85d78ba37b57964f895
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947670"
---
# <a name="implement-an-expression-evaluator"></a>Implementieren einer Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Das Auswerten eines Ausdrucks ist ein komplexes Zusammenspiel zwischen der Debug-Engine (de), dem Symbol Anbieter (SP), dem Binder Objekt und der Ausdrucks Auswertung (EE). Diese vier Komponenten sind Durchschnitt stellen verbunden, die von einer Komponente implementiert und von einer anderen Komponente genutzt werden.

 Der EE nimmt einen Ausdruck aus der de in Form einer Zeichenfolge an und analysiert oder wertet ihn aus. Der EE führt die folgenden Schnittstellen aus, die von de verwendet werden:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  Der EE Ruft das Binder Objekt auf, das von der de zur Verfügung gestellt wird, um den Wert von Symbolen und Objekten zu erhalten. Der EE verwendet die folgenden Schnittstellen, die von der de implementiert werden:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Der EE führt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)aus. `IDebugProperty2` stellt den Mechanismus bereit, mit dem das Ergebnis einer Ausdrucks Auswertung beschrieben wird, z. b. eine lokale Variable, ein primitiver oder ein Objekt in Visual Studio, das **dann die entsprechenden** Informationen im Fenster Lokal, über **Wachen** oder **direkt** anzeigt.

  Die SP wird dem ee von der "de" übergeben, wenn Sie Informationen anfordert. Der SP führt Schnittstellen aus, die Adressen und Felder beschreiben, wie z. b. die folgenden Schnittstellen und deren Ableitungen:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  Der EE nutzt alle diese Schnittstellen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementierungsstrategie für die Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definiert einen dreistufigen Prozess für die Strategie zur Implementierung der Ausdrucks Auswertung (EE Auswertung, EE).

## <a name="see-also"></a>Weitere Informationen
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
