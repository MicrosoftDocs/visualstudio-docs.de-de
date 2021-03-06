---
description: Enthält Statusinformationen zu Symbol Suchpfaden, die durchsucht wurden.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc914334fc4b8ebf2dd73f691cdec242e19364a9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222288"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Enthält Statusinformationen zu Symbol Suchpfaden, die durchsucht wurden.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Members

`dwValidFields`\
Eine Kombination von Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die die Art der Suchinformationen angibt, die in dieser Struktur beschrieben werden.

`bstrVerboseSearchInfo`\
Suchpfad und Ergebnisse werden zu einer einzelnen Zeichenfolge verkettet.

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird von einem Aufrufen der [getsymbolinfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) -Methode zurückgegeben.

Wenn das `bstrVerboseSearchInfo` Feld nicht leer ist, enthält es eine Liste der durchsuchten Pfade und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von einem Auslassungs Zeichen ("..."), gefolgt vom Ergebnis formatiert. Wenn mehr als ein Pfad Ergebnis Paar vorhanden ist, wird jedes Paar durch das Paar "\r\n" (Wagen Rücklauf/Zeilenvorschub) getrennt. Das Muster sieht wie folgt aus:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Beachten Sie, dass der letzte Eintrag keine \r\n-Sequenz hat.

Hier ist eine mögliche `bstrVerboseSearchInfo` Zeichenfolge, die an Standard out gesendet wurde.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Anforderungen

Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
