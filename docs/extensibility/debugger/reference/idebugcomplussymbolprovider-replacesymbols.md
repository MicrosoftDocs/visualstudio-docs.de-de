---
title: 'Idebugcomplussymbolprovider:: replacesymbols | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ReplaceSymbols
- IDebugComPlusSymbolProvider::ReplaceSymbols
ms.assetid: 82fbc8db-c4b1-432f-bec9-1a9dc09570be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90ef0ae096618b776182b397d196f2a4477abe5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733606"
---
# <a name="idebugcomplussymbolproviderreplacesymbols"></a>IDebugComPlusSymbolProvider::ReplaceSymbols
Ersetzt die aktuellen Debugsymbole durch die im angegebenen Datenstream.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ReplaceSymbols(
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    IStream* pStream
);
```

```csharp
int ReplaceSymbols(
    uint    ulAppDomainID,
    Guid    guidModule,
    IStream pStream
);
```

## <a name="parameters"></a>Parameter
`ulAppDomainID`\
in Der Bezeichner der Anwendungsdomäne.

`guidModule`\
in Eindeutiger Bezeichner des Moduls.

`pStream`\
in Datenstrom, der die neuen Symbole enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::ReplaceSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pStream
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::ReplaceSymbols );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->ReplaceSymbols( pStream ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::ReplaceSymbols, hr );
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
