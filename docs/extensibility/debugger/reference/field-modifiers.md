---
title: FIELD_MODIFIERS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5589b1535fbe22f0b0c1f2f9c9e34f70a4e7e861
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874321"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Gibt modifiziererer für einen Feldtyp an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Felder
`FIELD_MOD_ACCESS_TYPE`\
Gibt an, dass auf das Feld nicht zugegriffen werden kann.

`FIELD_MOD_ACCESS_PUBLIC`\
Gibt an, dass das Feld über öffentlichen Zugriff verfügt.

`FIELD_MOD_ACCESS_PROTECTED`\
Gibt an, dass das Feld geschützten Zugriff hat.

`FIELD_MOD_ACCESS_PRIVATE`\
Gibt an, dass das Feld über privaten Zugriff verfügt.

`FIELD_MOD_NOMODIFIERS`\
Gibt an, dass das Feld keine modifiziererer aufweist.

`FIELD_MOD_STATIC`\
Gibt an, dass das Feld statisch ist.

`FIELD_MOD_CONSTANT`\
Gibt an, dass das Feld eine Konstante ist.

`FIELD_MOD_TRANSIENT`\
Gibt an, dass das Feld vorübergehend ist.

`FIELD_MOD_VOLATILE`\
Gibt an, dass das Feld flüchtig ist.

`FIELD_MOD_ABSTRACT`\
Gibt an, dass das Feld abstrakt ist.

`FIELD_MOD_NATIVE`\
Gibt an, dass das Feld nativ ist.

`FIELD_MOD_SYNCHRONIZED`\
Gibt an, dass das Feld synchronisiert ist.

`FIELD_MOD_VIRTUAL`\
Gibt an, dass das Feld virtuell ist.

`FIELD_MOD_INTERFACE`\
Gibt an, dass das Feld eine Schnittstelle ist.

`FIELD_MOD_FINAL`\
Gibt an, dass das Feld endgültig ist.

`FIELD_MOD_SENTINEL`\
Gibt an, dass das Feld ein Sentinel ist.

`FIELD_MOD_INNERCLASS`\
Gibt an, dass das Feld eine innere Klasse ist.

`FIELD_TYPE_OPTIONAL`\
Gibt an, dass das Feld optional ist.

`FIELD_MOD_BYREF`\
Gibt an, dass das Feld ein Verweis Argument ist. Dies gilt insbesondere für Methodenargumente.

`FIELD_MOD_HIDDEN`\
Gibt an, dass das Feld ausgeblendet oder in einem anderen Kontext dargestellt werden muss. beispielsweise [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statische lokale Variablen.

`FIELD_MOD_MARSHALASOBJECT`\
Gibt an, dass das Feld ein Objekt mit einer- `IUnknown` Schnittstelle darstellt.

`FIELD_MOD_SPECIAL_NAME`\
Gibt an, dass das Feld einen speziellen Namen hat, z `.ctor` . b. für einen Konstruktor ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] nur).

`FIELD_MOD_HIDEBYSIG`\
Gibt an, dass das-Feld das- `Overloads` Schlüsselwort angewendet hat ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] nur).

`FIELD_MOD_WRITEONLY`\
Gibt an, dass das Feld schreibgeschützt ist. Dieser Wert ist nicht in enthalten `FIELD_MOD_ALL` , da die einzige Verwendung von schreibgeschützten Feldern für die Funktions Auswertung gilt. Ein Benutzer muss explizit Felder anfordern `FIELD_MOD_WRITEONLY` .

`FIELD_MOD_ACCESS_MASK`\
Gibt eine Maske für den Feld Zugriff an.

`FIELD_MOD_MASK`\
Gibt eine Maske für Feldmodifizierer an.

## <a name="remarks"></a>Bemerkungen
Wird für den `dwModifiers` Member der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) -Struktur verwendet.

Diese Werte werden auch an die [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) -Methode zum Filtern nach bestimmten Feldern übermittelt.

## <a name="requirements"></a>Anforderungen
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
