---
title: Evalflags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 073dac8de37edddc1b748c52258047cd2d85e218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937074"
---
# <a name="evalflags"></a>EVALFLAGS
Gibt Flags an, die die Ausdrucks Auswertung steuern.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Felder
`EVAL_RETURNVALUE`\
Gibt an, dass der Rückgabewert (sofern vorhanden) ausgewertet werden soll.

`EVAL_NOSIDEEFFECTS`\
Gibt an, dass Nebeneffekte nicht zulässig sind.

`EVAL_ALLOWBPS`\
Gibt an, dass Haltepunkte angehalten werden.

`EVAL_ALLOWERRORREPORT`\
Gibt an, dass die Fehlerberichterstattung an den Host zulässig ist. Wird hauptsächlich für die Ausdrucks Auswertung in Skripts in Internet Explorer verwendet.

`EVAL_FUNCTION_AS_ADDRESS`\
Erzwingt, dass Funktionen als Adressen ausgewertet werden, anstatt die Funktion aufzurufen.

`EVAL_NOFUNCEVAL`\
Verhindert, dass die Funktion ausgewertet wird. Sehen Sie sich beispielsweise das `int` Token im Ausdruck an `myExpression(int) + 10` . Diese Funktion kann ordnungsgemäß als Adresse ausgewertet werden, aber nicht als Wert.

`EVAL_NOEVENTS`\
Flag, das anzeigt, dass Ereignisse, die während der Ausdrucks Auswertung auftreten, nicht an den Sitzungs-Debug-Manager (SDM) oder an die IDE gesendet werden sollen.

## <a name="remarks"></a>Bemerkungen
Diese Flags werden als Argument an die Methoden [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) und [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) übermittelt.

Diese Flags können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
