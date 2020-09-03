---
title: IDebugExceptionEvent2::P asstodebug | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729830"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Gibt an, ob die Ausnahme an das Programm weitergegeben werden soll, das beim Fortsetzen der Ausführung deentschlgt wird, oder, wenn die Ausnahme verworfen werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parameter
`fPass`\
in Ungleich NULL ( `TRUE` ), wenn die Ausnahme an das Programm weitergegeben werden soll, das beim Fortsetzen der Ausführung deentschlgt wird, oder 0 (NULL `FALSE` ) (), wenn die Ausnahme verworfen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das Aufrufen dieser Methode führt nicht dazu, dass Code in dem Programm ausgeführt wird, das gedeppt wird. Der-Befehl besteht lediglich darin, den Zustand für die nächste Codeausführung festzulegen. Aufrufe der [canpasstodebuggende](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) -Methode können z `S_OK` . b. mit dem [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)zurückgeben.`dwState` das Feld ist auf festgelegt `EXCEPTION_STOP_SECOND_CHANCE` .

 Die IDE empfängt möglicherweise das [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) -Ereignis und ruft die [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) -Methode auf. Die Debug-Engine (de) sollte ein Standardverhalten aufweisen, um den Fall zu behandeln, wenn die `PassToDebuggee` Methode nicht aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
