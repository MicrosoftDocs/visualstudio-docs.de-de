---
description: Legt die Treffer Anzahl für den gebundenen Haltepunkt fest.
title: 'IDebugBoundBreakpoint2:: Abbild Anzahl | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7dbba43563a87a6c434d24014ce773375cd705c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167515"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Legt die Treffer Anzahl für den gebundenen Haltepunkt fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Parameter
`dwHitCount`\
in Die festzulegende Treffer Anzahl.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück `E_BP_DELETED` , wenn der Zustand des gebundenen Haltepunkt Objekts auf festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).

## <a name="remarks"></a>Bemerkungen
 Die Treffer Anzahl gibt an, wie oft dieser Haltepunkt während der aktuellen Sitzung der Sitzung ausgelöst wurde.

 Diese Methode wird in der Regel von der Debug-Engine aufgerufen, um die aktuelle Treffer Anzahl an diesem Breakpoint zu aktualisieren.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
