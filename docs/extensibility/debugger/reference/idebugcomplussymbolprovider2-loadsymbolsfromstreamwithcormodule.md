---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
- LoadSymbolsFromStreamWithCorModule
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e3e3251c80b3381bbc44480cc5ca3d9884ac850
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743021"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromstreamwithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
Lädt Debugsymbole aus einem Datenstrom, wenn das **ICorDebugModule** -Objekt angegeben ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbolsFromStreamWithCorModule(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStreamWithCorModule(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    object  pUnkCorDebugModule,
    IStream pStream
);
```

## <a name="parameters"></a>Parameter
`ulAppDomainID`\
in Der Bezeichner der Anwendungsdomäne.

`guidModule`\
in Eindeutiger Bezeichner des Moduls.

`baseAddress`\
in Basis Speicheradresse.

`pUnkMetadataImport`\
in Ein-Objekt, das die Symbol Metadaten enthält.

`pUnkCorDebugModule`\
in Objekt, das die [ICorDebug Module-Schnittstelle](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface)implementiert.

`pStream`\
in Datenstream, der die zu ladenden Debugsymbole enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    IStream* pStream
)
{
    CAutoLock Lock(this);

    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<ICorDebugModule> pCorModule;

    CModule* pmodule = NULL;
    CModule* pmoduleNew = NULL;
    bool fAlreadyLoaded = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    DWORD dwCurrentState = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );

    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );

    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**)&pMetadata) );

    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,
              (void**)&pCorModule) );

    ASSERT(guidModule != GUID_NULL);

    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;

    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );

    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;

    IfFailGo( pmoduleNew->Create( idModule,
                                  dwCurrentState,
                                  pMetadata,
                                  pCorModule,
                                  pStream,
                                  baseOffset ) );

    if (fAlreadyLoaded)
    {
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));
        RemoveModule(pmodule);
    }

    IfFailGo( AddModule( pmoduleNew ) );

Error:

    RELEASE (pmodule);
    RELEASE (pmoduleNew);

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
