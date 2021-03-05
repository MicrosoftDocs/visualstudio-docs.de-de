---
description: Ruft den Haltepunkt-Stellungstyp dieser Haltepunkt Anforderung ab.
title: 'IDebugBreakpointRequest2:: getlocationtype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed19d65fc0c29b8cd97b607a0748c48ad52783b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143375"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
Ruft den Haltepunkt-Stellungstyp dieser Haltepunkt Anforderung ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLocationType(
    BP_LOCATION_TYPE* pBPLocationType
);
```

```csharp
int GetLocationType(
    out enum_BP_LOCATION_TYPE pBPLocationType
);
```

## <a name="parameters"></a>Parameter
`pBPLocationType`\
vorgenommen Gibt einen Wert aus der [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) -Enumeration zurück, der den Speicherort dieser Haltepunkt Anforderung beschreibt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_FAIL` Wenn das `bpLocation` Feld in der zugeordneten [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur ungültig ist.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CDebugBreakpointRequest` , das die[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Schnittstelle verfügbar macht.

```
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)
{
    HRESULT hr;

    if (pBPLocationType)
    {
        // Set default BP_LOCATION_TYPE.
        *pBPLocationType = BPLT_NONE;

        // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.
        if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))
        {
            // Get the new BP_LOCATION_TYPE.
            *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
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
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
