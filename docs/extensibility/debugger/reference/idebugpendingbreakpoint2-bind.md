---
description: Bindet diesen ausstehenden Breakpoint an einen oder mehrere Code Speicherorte.
title: 'IDebugPendingBreakpoint2:: Bind | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eda2cdef924aec782b18155a92e3a0159b338f08
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143114"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
Bindet diesen ausstehenden Breakpoint an einen oder mehrere Code Speicherorte.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Bind( 
   void 
);
```

```csharp
int Bind();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_BP_DELETED` Wenn der Breakpoint gelöscht wurde.

## <a name="remarks"></a>Bemerkungen
 Wenn diese Methode aufgerufen wird, sollte eine Debug-Engine (de) versuchen, diesen ausstehenden Haltepunkt an alle Code Positionen zu binden, die mit identisch sind.

 Nachdem diese Methode zurückgegeben wurde, muss der Aufrufer auf Ereignisse warten, die angeben, dass der ausstehende Haltepunkt gebunden wurde oder einen Fehler aufweist, bevor angenommen wird, dass Aufrufe von [enumboundbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) oder [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).-Methoden alle gebundenen bzw. Fehler Breakpunkte auflisten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
