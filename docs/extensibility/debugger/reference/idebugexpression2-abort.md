---
title: 'IDebugExpression2:: Abort | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18e0e4b810e76bd5c5de7b0f8d77e7cd72ceb565
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901695"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Diese Methode bricht die asynchrone Ausdrucks Auswertung ab, wie durch einen-Aufrufvorgang der [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methode gestartet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn die asynchrone Ausdrucks Auswertung abgebrochen wird, senden Sie kein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Ereignis an den Ereignis Rückruf, der an die [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) -oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methoden übermittelt wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
