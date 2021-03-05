---
description: Legt die mit diesem gebundenen Haltepunkt verknüpfte Durchlauf Anzahl fest oder ändert diese.
title: 'IDebugBoundBreakpoint2:: setpasscount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ccefd1e3b120ac52801a1163ea8bda814626a0b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167489"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Legt die mit diesem gebundenen Haltepunkt verknüpfte Durchlauf Anzahl fest oder ändert diese.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parameter
`bpPassCount`\
in Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die die Durchlauf Anzahl angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück `E_BP_DELETED` , wenn der Zustand des gebundenen Haltepunkt Objekts auf festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).

## <a name="remarks"></a>Bemerkungen
 Der Durchlauf Zähler bestimmt, wann der Breakpoint ausgelöst wird. Die aktuelle Durchlauf-oder Treffer Anzahl kann durch Aufrufen der [gethitcount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) -Methode abgerufen werden.

 Jeder Durchlauf Zähler, der zuvor mit diesem Breakpoint verknüpft war, geht verloren.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
