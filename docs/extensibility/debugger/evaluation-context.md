---
title: Auswertungs Kontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738800"
---
# <a name="evaluation-context"></a>Evaluierungskontext
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn die Debug-Engine (de) die Ausdrucks Auswertung (EE) aufruft, bestimmen drei Argumente, die an [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) weitergegeben werden, den Kontext zum Suchen und Auswerten von Symbolen, wie in der folgenden Tabelle dargestellt.

## <a name="arguments"></a>Argumente

|Argument|Beschreibung|
|--------------|-----------------|
|`pSymbolProvider`|Eine [idebugsymbolprovider](../../extensibility/debugger/reference/idebugsymbolprovider.md) -Schnittstelle, die den Symbol Handler (SH) angibt, der zum Identifizieren des Symbols verwendet werden soll.|
|`pAddress`|Eine [idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle, die den aktuellen Ausführungs Punkt angibt. Diese Schnittstelle findet die Methode, die den ausgeführten Code enthält.|
|`pBinder`|Eine [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, die den Wert und den Typ eines Symbols anhand seines Namens findet.|

 `IDebugParsedExpression::EvaluateSync` gibt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurück, die den resultierenden Wert und seinen Typ darstellt.

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Schlüssel Ausdrucks Auswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
