---
title: FIELD_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f358c6c9a192ddd4d71f26a0f2f795ae012bc2c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941839"
---
# <a name="field_info"></a>FIELD_INFO
Diese Struktur beschreibt eine lokale Variable, einen Parameter oder ein anderes Feld.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von Flags aus der [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Enumeration, die angibt, welche Member ausgefüllt werden.

`bstrFullName`\
Der vollständige Name des Felds.

`bstrName`\
Der Kurzname des Felds.

`bstrType`\
Der Typ des Felds.

`dwModifiers`\
Eine Kombination von Flags aus der [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Enumeration, die das Feld beschreibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) -Methode, in der Sie ausgefüllt ist, übermittelt.

## <a name="requirements"></a>Anforderungen
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
