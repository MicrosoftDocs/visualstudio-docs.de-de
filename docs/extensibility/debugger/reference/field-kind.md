---
description: Gibt die Art des Felds an, das in einem idebugfield-Objekt enthalten ist.
title: FIELD_KIND | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 519b18f9e4b0329ded9b17ec0152f36e37377df0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150860"
---
# <a name="field_kind"></a>FIELD_KIND
Gibt die Art des Felds an, das in einem [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt enthalten ist.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Felder
`FIELD_KIND_TYPE`\
Gibt an, dass das Feld nur einen-Typ ist.

`FIELD_KIND_SYMBOL`\
Gibt an, dass das Feld ein Symbol mit Typ, Name und anderen Informationen ist.

`FIELD_TYPE_PRIMITIVE`\
Gibt an, dass das Feld ein primitiver Datentyp ist.

`FIELD_TYPE_STRUCT`\
Gibt an, dass das Feld eine Struktur ist.

`FIELD_TYPE_CLASS`\
Gibt an, dass das Feld eine Klasse ist.

`FIELD_TYPE_INTERFACE`\
Gibt an, dass das Feld eine Schnittstelle ist.

`FIELD_TYPE_UNION`\
Gibt an, dass das Feld eine Union ist.

`FIELD_TYPE_ARRAY`\
Gibt an, dass das Feld ein Array ist.

`FIELD_TYPE_METHOD`\
Gibt an, dass das Feld eine Methode ist.

`FIELD_TYPE_BLOCK`\
Gibt an, dass das Feld ein Block ist.

`FIELD_TYPE_POINTER`\
Gibt an, dass das Feld ein Zeiger ist.

`FIELD_TYPE_ENUM`\
Gibt an, dass das Feld ein enumerierter Datentyp ist.

`FIELD_TYPE_LABEL`\
Gibt an, dass das Feld eine Bezeichnung ist.

`FIELD_TYPE_TYPEDEF`\
Gibt an, dass das Feld eine Typdefinition ist.

`FIELD_TYPE_BITFIELD`\
Gibt an, dass das Feld ein Bitfeld ist.

`FIELD_TYPE_NAMESPACE`\
Gibt an, dass das Feld ein Namespace ist.

`FIELD_TYPE_MODULE`\
Gibt an, dass das Feld ein Modul ist.

`FIELD_TYPE_DYNAMIC`\
Gibt an, dass das Feld dynamisch ist.

`FIELD_TYPE_PROP`\
Gibt an, dass das Feld eine Eigenschaft ist.

`FIELD_TYPE_INNERCLASS`\
Gibt an, dass das Feld eine innere Klasse ist.

`FIELD_TYPE_REFERENCE`\
Gibt an, dass das Feld ein Verweis ist.

`FIELD_TYPE_EXTENDED`\
Für zukünftige Verwendung reserviert.

`FIELD_SYM_MEMBER`\
Gibt an, dass das Feld ein Member ist.

`FIELD_SYM_LOCAL`\
Gibt an, dass das Feld lokal ist.

`FIELD_SYM_PARAMETER`\
Gibt an, dass das Feld ein Parameter ist.

`FIELD_SYM_THIS`\
Gibt an, dass das Feld der "This"-Zeiger ist.

`FIELD_SYM_GLOBAL`\
Gibt an, dass das Feld Global ist.

`FIELD_SYM_PROP_GETTER`\
Gibt an, dass das Feldeigenschaften abruft.

`FIELD_SYM_PROP_SETTER`\
Gibt an, dass das Feldeigenschaften festlegt.

`FIELD_SYM_EXTENDED`\
Für zukünftige Verwendung reserviert.

`FIELD_KIND_MASK`\
Gibt eine Maske für Feldarten an.

`FIELD_TYPE_MASK`\
Gibt eine Maske für Feldtypen an.

`FIELD_SYM_MASK`\
Gibt eine Maske für Symbol Informationen an.

## <a name="remarks"></a>Bemerkungen
Wird von einem Aufrufen der [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode zurückgegeben.

Abhängig von der Art des Felds kann [QueryInterface](/cpp/atl/queryinterface) für die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle aufgerufen werden, um eine spezifischere Form der-Schnittstelle zu erhalten. Wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) z. b. zurückgibt `FIELD_TYPE_METHOD` , können Sie `QueryInterface` auf ich aufrufen, `DebugField` um die [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Schnittstelle abzurufen.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
