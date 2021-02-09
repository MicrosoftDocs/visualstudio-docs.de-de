---
title: 'IDebugThread2:: getthreadproperties | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadProperties
helpviewer_keywords:
- IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c547ad049fa36231ce108a6cfc406233b972ff2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893775"
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Ruft die Eigenschaften ab, die diesen Thread beschreiben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetThreadProperties (
    THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES*     ptp
);
```

```csharp
int GetThreadProperties (
    enum_THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES[]         ptp
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
in Eine Kombination von Flags aus der [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Enumeration, die bestimmt, welche Felder von `ptp` ausgefüllt werden sollen.

`ptp`\
[in, out] Eine [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur, die mit den Eigenschaften des Threads ausgefüllt ist.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Die von dieser Methode zurückgegebenen Informationen werden in der Regel im Fenster **Threads** Debuggen angezeigt.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches `CProgram` Objekt implementiert wird, das die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Schnittstelle implementiert.

```cpp
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,
                                      THREADPROPERTIES *ptp)
{
    HRESULT hr = E_FAIL;

    // Check for valid argument.
    if (ptp)
    {
        // Create an array of buffers at ptp the size of the
        // THREADPROPERTIES structure and set all of the
        // buffers at ptp to 0.
        memset(ptp, 0, sizeof (THREADPROPERTIES));

        // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.
        if (dwFields & TPF_ID)
        {
            // Check for successful assignment of the current thread ID to
            // the dwThreadId of the passed THREADPROPERTIES.
            if (GetThreadId(&(ptp->dwThreadId)) == S_OK)
            {
                // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator
                // of the passed THREADPROPERTIES.
                ptp->dwFields |= TPF_ID;
            }
        }

        hr = S_OK;
    }
    else
        hr = E_INVALIDARG;

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
