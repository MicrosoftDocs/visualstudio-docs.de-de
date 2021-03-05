---
description: Ruft den ausstehenden Breakpoint ab, von dem der angegebene gebundene Breakpoint erstellt wurde.
title: 'IDebugBoundBreakpoint2:: getpdingbreakpoint | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18b6ab7f9c520511d2abe57e3864e71bc7534b4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167580"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
Ruft den ausstehenden Breakpoint ab, von dem der angegebene gebundene Breakpoint erstellt wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPendingBreakpoint( 
    IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint( 
    out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>Parameter
`ppPendingBreakpoint`\
vorgenommen Gibt das [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt zurück, das den ausstehenden Haltepunkt darstellt, der zum Erstellen dieses gebundenen halte Punkts verwendet wurde.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Ein ausstehender Haltepunkt kann als eine Auflistung aller erforderlichen Informationen angesehen werden, die erforderlich sind, um einen Breakpoint an Code zu binden, der auf ein oder mehrere Programme angewendet werden kann.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CBoundBreakpoint` , das die [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) -Schnittstelle verfügbar macht.

```
HRESULT CBoundBreakpoint::GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBreakpoint)
{
    HRESULT hr;

    // Check for valid IDebugPendingBreakpoint2 interface pointer.
    if (ppPendingBreakpoint)
    {
        // Be sure that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugPendingBreakpoint2 interface.
            hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,
                                              (void**)ppPendingBreakpoint);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
