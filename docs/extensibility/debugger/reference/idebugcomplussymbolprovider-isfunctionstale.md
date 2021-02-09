---
title: 'Idebugcomplussymbolprovider:: isfunctionstale | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionStale
ms.assetid: dcffc090-4ed8-47b2-ba51-bce1a6b6428d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 577ad48603c1378e8d34390f9780620ddbecb573
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892852"
---
# <a name="idebugcomplussymbolproviderisfunctionstale"></a>IDebugComPlusSymbolProvider::IsFunctionStale
Bestimmt, ob die Funktion an der angegebenen debugadresse als veraltet eingestuft wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsFunctionStale(
    IDebugAddress* pAddress
);
```

```csharp
int IsFunctionStale(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Die Debug-Adresse, die durch eine [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird. Bei dieser Adresse muss es sich um einen METHOD_ADDRESS handeln.

## <a name="return-value"></a>Rückgabewert
Wenn die Funktion als veraltet eingestuft wird, wird zurückgegeben `S_OK` . Wenn die-Funktion nicht veraltet ist, wird zurückgegeben `S_FALSE` .

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::IsFunctionStale(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionStale );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsFunctionStale( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion ))
    {

        // S_FALSE indicates the function is not stale

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsFunctionStale, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
