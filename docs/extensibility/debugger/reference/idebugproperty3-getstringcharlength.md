---
title: 'IDebugProperty3:: getstringcharlength | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3189a7c84ed36827ab48b27c8f727314eb34983
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963119"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
Gibt die Anzahl von Zeichen in der Zeichenfolge der zugeordneten Eigenschaft zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetStringCharLength(
    ULONG *pLen
);
```

```csharp
int GetStringCharLength(
    out uint pLen
);
```

## <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|`pLen`|vorgenommen Gibt die Anzahl von Zeichen in der Zeichenfolge der Eigenschaft zurück.|

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
In der Regel wird diese Methode als Auftakt verwendet, um einen Puffer für einen Aufrufen der [getstringchars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) -Methode zuzuordnen.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cproperty** -Objekt implementiert wird, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle verfügbar macht.

```cpp
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)
{
    HRESULT hr = E_INVALIDARG;

    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;

    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;

    if (pLen)
    {
        DEBUG_PROPERTY_INFO dpInfo;
        dpInfo.bstrValue = NULL;
        ULONG ulen = 0;
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);
        if (hr == S_OK && dpInfo.bstrValue)
        {
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)
            {
                ulen = 0; //VSWhidbey#64815
            }
            else
            {
                ulen = ::SysStringLen(dpInfo.bstrValue);
                if( ulen > 2 &&
                    dpInfo.bstrValue[0] == L'"' &&
                    dpInfo.bstrValue[ulen-1] == L'"')
                {
                    ulen = ulen > 2 ? ulen - 2 : ulen; //remove two double quotes
                }
            }
        }
        ::SysFreeString(dpInfo.bstrValue);
        *pLen = ulen;
    }
    m_EVALFLAGS = oldEVALFLAGS;
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
