---
description: Diese Schnittstelle stellt einen Symbol Anbieter dar, der Symbole und Typen bereitstellt und Sie als Felder zurückgibt.
title: Idebugsymbolprovider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0488520f8bde0ccd2638636810cb0055a7f3f4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168425"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Diese Schnittstelle stellt einen Symbol Anbieter dar, der Symbole und Typen bereitstellt und Sie als Felder zurückgibt.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein Symbol Anbieter muss diese Schnittstelle implementieren, um der Ausdrucks Auswertung Symbol-und Typinformationen bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Diese Schnittstelle wird mithilfe der com- `CoCreateInstance` Funktion (bei nicht verwalteten Symbol Anbietern) oder durch das Laden der entsprechenden verwalteten Codeassembly und durch das Instanziieren des Symbol Anbieters basierend auf den in dieser Assembly gefundenen Informationen abgerufen. Die Debug-Engine instanziiert den Symbol Anbieter für die Koordination mit der Ausdrucks Auswertung. Sehen Sie sich das Beispiel für einen Ansatz zum Instanziieren dieser Schnittstelle an.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugSymbolProvider` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|`Initialize`|Veraltet. Nicht verwenden.|
|`Uninitialize`|Veraltet. Nicht verwenden.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ruft das Feld ab, das die debugadresse enthält.|
|`GetField`|Veraltet. Nicht verwenden.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Ordnet eine Dokument Position einem Array von debugadressen zu.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Ordnet einen Dokument Kontext einem Array von debugadressen zu.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Ordnet eine debugadresse einem Dokument Kontext zu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ruft die Sprache ab, die zum Kompilieren des Codes an der debugadresse verwendet wird.|
|`GetGlobalContainer`|Veraltet. Nicht verwenden.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ruft das Feld ab, das einen voll qualifizierten Methodennamen darstellt.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ruft den Klassen Feldtyp ab, der einen voll qualifizierten Klassennamen darstellt.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Erstellt einen Enumerator für Namespaces, die der Debug-Adresse zugeordnet sind.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Ordnet einem Symboltyp einen Symbolnamen zu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ruft die debugadresse ab, die einer bestimmten debugadresse in einer Methode folgt.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle ordnet Dokument Positionen debugadressen zu und umgekehrt.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie der Symbol Anbieter bei Angabe der GUID instanziiert wird (eine Debug-Engine muss diesen Wert kennen).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
