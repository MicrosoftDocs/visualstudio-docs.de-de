---
title: METADATA_ADDRESS_FIELD | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 686eeff2012c02442d166966fff32abc0b1cdf32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961975"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD

Diese Struktur stellt die Adresse eines Felds einer Klasse oder Struktur dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_FIELD {
    _mdToken tokField;
} METADATA_ADDRESS_FIELD
```

```csharp
public struct METADATA_ADDRESS_FIELD {
    public int tokField;
}
```

## <a name="members"></a>Member

`tokField`\
Die ID des Feld Tokens.

[C++] `_mdToken` ist eine `typedef` für ein 32-Bit- `int` .

## <a name="remarks"></a>Bemerkungen

Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, wenn das- `dwKind` Feld der- `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_FIELD` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration).

## <a name="requirements"></a>Anforderungen

Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
