---
title: 'Idebugcomplussymbolprovider:: getfunctionlineoffset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetFunctionLineOffset
- GetFunctionLineOffset
ms.assetid: 51460f5a-4e98-427a-8315-27246e24fb61
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42e11e527f31835a22273a2b8c31b90f231a9316
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880917"
---
# <a name="idebugcomplussymbolprovidergetfunctionlineoffset"></a>IDebugComPlusSymbolProvider::GetFunctionLineOffset
Ruft die Adresse innerhalb einer Funktion ab, die den angegebenen Zeilen Offset darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetFunctionLineOffset(
    IDebugAddress*  pAddress,
    DWORD           dwLine,
    IDebugAddress** ppNewAddress
);
```

```csharp
int GetFunctionLineOffset(
    IDebugAddress     pAddress,
    uint              dwLine,
    out IDebugAddress ppNewAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Adresse, die die Funktion darstellt.

`dwLine`\
in Zeilen Offset vom Anfang der Funktion.

`ppNewAddress`\
vorgenommen Neue Adresse, die den Zeilen Offset vom Anfang der Funktion darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::GetFunctionLineOffset(
    IDebugAddress *pAddress,
    DWORD dwLine,
    IDebugAddress **ppNewAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;
    DWORD dwOffset;
    CDebugAddress* paddr = NULL;

    METHOD_ENTRY(CDebugSymbolProvider::GetFunctionLineOffset);

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    // Find the first offset for dwLine in the function

    IfFailGo( pModule->GetFunctionLineOffset( address.addr.addr.addrMethod.tokMethod,
              address.addr.addr.addrMethod.dwVersion,
              dwLine,
              &dwOffset ) );

    // Create the new Address

    address.addr.addr.addrMethod.dwOffset = dwOffset;
    IfNullGo( paddr = new CDebugAddress(address), E_OUTOFMEMORY );
    IfFailGo( paddr->QueryInterface( __uuidof(IDebugAddress),
                                     (void**) ppNewAddress ) );

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetFunctionLineOffset, hr);
    RELEASE( paddr );
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
