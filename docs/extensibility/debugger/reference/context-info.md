---
title: CONTEXT_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737567"
---
# <a name="context_info"></a>CONTEXT_INFO
Diese Struktur beschreibt einen Speicher Kontext oder Code Kontext.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von Flags von der [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) -Enumeration, die angibt, welche Felder ausgefüllt werden<strong>.</strong>

`bstrModuleUrl`\
Der Name des Moduls, in dem sich der Kontext befindet.

`bstrFunction`\
Der Name der Funktion, in der sich der Kontext befindet.

`posFunctionOffset`\
Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die die Zeilen-und Spalten Abweichung der Funktion identifiziert, die dem Code Kontext zugeordnet ist.

`bstrAddress`\
Die Adresse im Code, in der sich der angegebene Kontext befindet.

`bstrAddressOffset`\
Der Offset der Adresse im Code, an dem sich der angegebene Kontext befindet.

`bstrAddressAbsolute`\
Die absolute Adresse im Speicher, in der sich der angegebene Kontext befindet.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von einem Aufrufen der [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) -Methode zurückgegeben.

Eine typische Verwendung für diese Struktur ist die Unterstützung eines **arbeitsspeicherdebugfensters** .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
