---
description: Legt die dem ausstehenden Breakpoint zugeordnete Bedingung fest oder ändert diese.
title: 'IDebugPendingBreakpoint2:: setcondition | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea2ce1a5a9ffdfb48e0190dc3399ceabf5cb052
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142894"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Legt die dem ausstehenden Breakpoint zugeordnete Bedingung fest oder ändert diese.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parameter
`bpCondition`\
in Eine [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur, die die festzulegende Bedingung angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jede Bedingung, die zuvor mit dem ausstehenden Breakpoint verknüpft war, geht verloren. Alle Haltepunkte, die von diesem ausstehenden Haltepunkt gebunden werden, werden aufgerufen, um die Bedingung auf den im-Parameter angegebenen Wert festzulegen `bpCondition` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
