---
title: 'Idebugcomplussymbolprovider:: getlocalvariablelayout | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0671715dd0532e268c6cc59abfafd62ff7686e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911975"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
Ruft das Layout von lokalen Variablen für einen Satz von Methoden ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLocalVariablelayout(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONG32   cMethods,
    _mdToken  rgMethodTokens[],
    IStream** pStreamLayout
);
```

```csharp
int GetLocalVariablelayout(
    uint        ulAppDomainID,
    Guid        guidModule,
    uint        cMethods,
    int[]       rgMethodTokens,
    out IStream pStreamLayout
);
```

## <a name="parameters"></a>Parameter
`ulAppDomainID`\
in Der Bezeichner der Anwendungsdomäne.

`guidModule`\
in Eindeutiger Bezeichner des Moduls.

`cMethods`\
in Anzahl der Methoden Token im `rgMethodTokens` Array.

`rgMethodTokens`\
in Array von Methoden Token.

`pStreamLayout`\
vorgenommen Ein Textstream, der das Variablen Layout enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONG32 cMethods,
    _mdToken rgMethodTokens[],
    IStream** ppStreamLayout)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);

    CComPtr<ISymUnmanagedReader> symReader;
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));
    CComPtr<IStream> stream;
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));

    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)
    {
        CComPtr<ISymUnmanagedMethod> method;
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));
        CComPtr<ISymUnmanagedScope> rootScope;
        IfFailRet(method->GetRootScope(&rootScope));

        //
        // Add the method's variables to the stream
        //
        IfFailRet(AddScopeToStream(rootScope, 0, stream));

        // do end of method marker
        ULONG32 depth = 0xFFFFFFFF;
        ULONG cb = 0;
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));
    }

    LARGE_INTEGER pos;
    pos.QuadPart = 0;
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));
    *ppStreamLayout = stream.Detach();

    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
