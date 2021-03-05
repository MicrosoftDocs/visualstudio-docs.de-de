---
description: Ruft den Namen des Moduls ab, das gerade deentschlgt wird.
title: 'IDebugBeforeSymbolSearchEvent2:: getmodulename | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c053bd14949a2688ad332207d07355333814a120
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167775"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
Ruft den Namen des Moduls ab, das gerade deentschlgt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetModuleName(
    BSTR *pbstrModuleName
);
```

```csharp
public int GetModuleName (
    string pbstrModuleName
);
```

## <a name="parameters"></a>Parameter
`pbstrModuleName`\
vorgenommen Der Name des Moduls.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugbeforesymbolsearcheventbase** -Objekt implementiert wird, das die [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) -Schnittstelle verfügbar macht.

```cpp
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)
{
    HRESULT hRes = E_FAIL;

    if (m_bstrModuleName)
    {

        *pbstrModuleName = SysAllocString( m_bstrModuleName);

        if (*pbstrModuleName)
        {
            hRes = S_OK;
        }
    }

    return ( hRes );
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)
