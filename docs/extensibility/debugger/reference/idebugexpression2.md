---
title: IDebugExpression2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d7b6508a635edf3dc328f79a06a386efce07aae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949583"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Diese Schnittstelle stellt einen analysierten Ausdruck dar, der für das Binden und auswerten bereit ist.

## <a name="syntax"></a>Syntax

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um einen analysierten Ausdruck darzustellen, der für die Auswertung bereit ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein [aufruftertext](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) gibt diese Schnittstelle zurück. [Getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle zurück. Diese Schnittstellen sind nur verfügbar, wenn das Programm, das gedebuggt wird, angehalten wurde und ein Stapel Rahmen verfügbar ist.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugExpression2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet diesen Ausdruck asynchron aus.|
|[Abbrechen](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucks Auswertung.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet diesen Ausdruck synchron aus.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Programm angehalten wurde, erhält der Sitzungs-Debug-Manager (SDM) einen Stapel Rahmen von der de mit einem aufzurufenden [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)-Aufrufs. Der SDM ruft dann [getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle zu erhalten. Darauf folgt ein aufruftertext [](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erstellen der- `IDebugExpression2` Schnittstelle, die den analysierten Ausdruck darstellt, der für die Auswertung bereit ist.

 Der SDM ruft entweder [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den Ausdruck tatsächlich auszuwerten und einen Wert zu erhalten.

 In einer Implementierung von `IDebugExpressionContext2::ParseText` verwendet de die com- `CoCreateInstance` Funktion, um eine Ausdrucks Auswertung zu instanziieren und eine [idebugexpressionevaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) -Schnittstelle zu erhalten (siehe das Beispiel in der- `IDebugExpressionEvaluator` Schnittstelle). Das de-Element [ruft dann](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) die Analyse auf, um eine [idebugparamesetdexpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) -Schnittstelle zu erhalten. Diese Schnittstelle wird in der Implementierung von `IDebugExpression2::EvaluateSync` und verwendet `IDebugExpression2::EvaluateAsync` , um die Auswertung durchzuführen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
