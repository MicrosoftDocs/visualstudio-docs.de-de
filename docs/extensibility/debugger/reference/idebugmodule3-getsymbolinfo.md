---
description: Ruft eine Liste der Pfade, die nach Symbolen durchsucht werden, sowie die Ergebnisse der Suche der einzelnen Pfade ab.
title: 'IDebugModule3:: getsymbolinfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2793c9b6d9d88997ce2e4e84c147f87183555cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164850"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Ruft eine Liste der Pfade, die nach Symbolen durchsucht werden, sowie die Ergebnisse der Suche der einzelnen Pfade ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
in Eine Kombination von Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die angibt, welche Felder von `pInfo` ausgefüllt werden sollen.

`pInfo`\
vorgenommen Eine [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) -Struktur, deren Member mit den angegebenen Informationen aufgefüllt werden sollen. Wenn dies ein NULL-Wert ist, gibt diese Methode zurück `E_INVALIDARG` .

## <a name="return-value"></a>Rückgabewert
Wenn die Methode erfolgreich ist, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben.

> [!NOTE]
> Die zurückgegebene Zeichenfolge (in der- `MODULE_SYMBOL_SEARCH_INFO` Struktur) kann leer sein, auch wenn `S_OK` zurückgegeben wird. In diesem Fall gab es keine Suchinformationen, die zurückgegeben werden konnten.

## <a name="remarks"></a>Bemerkungen
Wenn das `bstrVerboseSearchInfo` -Feld der `MODULE_SYMBOL_SEARCH_INFO` -Struktur nicht leer ist, enthält es eine Liste der durchsuchten Pfade und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von einem Auslassungs Zeichen ("..."), gefolgt vom Ergebnis formatiert. Wenn mehr als ein Pfad Ergebnis Paar vorhanden ist, wird jedes Paar durch das Paar "\r\n" (Wagen Rücklauf/Zeilenvorschub) getrennt. Das Muster sieht wie folgt aus:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Beachten Sie, dass der letzte Eintrag keine \r\n-Sequenz hat.

## <a name="example"></a>Beispiel
In diesem Beispiel gibt diese Methode drei Pfade mit drei unterschiedlichen Suchergebnissen zurück. Jede Zeile wird mit einem Wagen Rücklauf/Zeilenvorschub Paar beendet. Die Beispielausgabe druckt nur die Suchergebnisse als eine einzelne Zeichenfolge.

> [!NOTE]
> Ein Status Ergebnis ist alles, das unmittelbar nach dem "..." bis zum Ende der Zeile.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb... Die Datei wurde nicht gefunden.** 
 **c:\winnt\symbols\user32.pdb... Die Version stimmt nicht mit ab.** 
 **\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Symbole geladen.**

## <a name="see-also"></a>Weitere Informationen

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
