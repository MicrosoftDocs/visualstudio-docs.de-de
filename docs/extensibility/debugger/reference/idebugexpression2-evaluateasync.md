---
description: Diese Methode wertet den Ausdruck asynchron aus.
title: 'IDebugExpression2:: evaluateasync | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7b01289c792e887c096d0a9068bac55b21a3a503
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152688"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Diese Methode wertet den Ausdruck asynchron aus.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parameter
`dwFlags`\
in Eine Kombination von Flags aus der [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die die Ausdrucks Auswertung steuern.

`pExprCallback`\
in Dieser Parameter ist immer ein NULL-Wert.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben. Ein typischer Fehlercode lautet wie folgt:

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Zurzeit wird ein anderer Ausdruck ausgewertet, und die gleichzeitige Auswertung von Ausdrücken wird nicht unterstützt.|

## <a name="remarks"></a>Bemerkungen
Diese Methode sollte sofort nach dem Start der Ausdrucks Auswertung zurückgegeben werden. Wenn der Ausdruck erfolgreich ausgewertet wird, muss ein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) an den [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Ereignis Rückruf gesendet werden, der durch [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)bereitgestellt wird.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches `CExpression` Objekt implementiert wird, das die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle implementiert.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
