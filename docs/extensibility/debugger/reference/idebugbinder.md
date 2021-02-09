---
title: Idebugbinder | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3cf4f418cf02f08f95d0192e99c0b02d0f74e3ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925111"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bindet ein Symbolfeld, das normalerweise vom Symbol Anbieter zurückgegeben wird, an einen Speicher Kontext oder ein Objekt, das den aktuellen Wert des Symbols enthält.

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle unterstützt die Auswertung von Ausdrücken und muss von der Debug-Engine (de) implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird im Prozess der Ausdrucks Auswertung verwendet und wird in der Regel in der Implementierung von [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBinder` .

|Methode|Beschreibung|
|------------|-----------------|
|[Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft den Arbeitsspeicher Kontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Lauf Zeittyp eines Objekts.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert einen Objekt Speicherort oder eine Speicheradresse in einen Speicher Kontext.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt ab, das zum Erstellen von Funktionsparametern verwendet wird.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den genauen Typ für eine Variable ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle gibt Objekte zurück, die von der Ausdrucks Auswertung in Analyse Strukturen verwendet werden. Die Ausdrucks Auswertung analysiert einen Ausdruck mithilfe des Symbol Anbieters, um die Symbole im Ausdruck in Instanzen von [idebugfield](../../../extensibility/debugger/reference/idebugfield.md)zu konvertieren, in denen jedes Symbol in Bezug auf den Typ und die Position im Quellcode beschrieben wird. Die [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode konvertiert `IDebugField` Objekte in [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekte, die einen Symboltyp mit einem tatsächlichen Wert im Arbeitsspeicher verbinden oder binden. Diese `IDebugObject` Objekte werden dann zur späteren Auswertung in einer Analyse Struktur gespeichert.

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
