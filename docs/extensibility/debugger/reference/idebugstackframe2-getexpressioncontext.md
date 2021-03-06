---
description: Ruft einen Auswertungs Kontext für die Ausdrucks Auswertung innerhalb des aktuellen Kontexts eines Stapel Rahmens und Threads ab.
title: 'IDebugStackFrame2:: getexpressioncontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4780b979102ee2ada499e2cd2e0f8ca728cadd91
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145936"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Ruft einen Auswertungs Kontext für die Ausdrucks Auswertung innerhalb des aktuellen Kontexts eines Stapel Rahmens und Threads ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Parameter
`ppExprCxt`\
vorgenommen Gibt ein [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Objekt zurück, das einen Kontext für die Ausdrucks Auswertung darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen kann ein Ausdrucks Auswertungs Kontext als Bereich zum Durchführen der Ausdrucks Auswertung betrachtet werden. Aufrufen der [Methode "](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode", um einen Ausdruck zu analysieren und dann die resultierenden [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) -oder [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methoden aufzurufen, um den analysierten Ausdruck auszuwerten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
