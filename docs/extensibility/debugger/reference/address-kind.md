---
description: Gibt die Arten von Adressen an.
title: ADDRESS_KIND | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12a47edf2b9eca9cd99a5b11531f78e080572d54
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144649"
---
# <a name="address_kind"></a>ADDRESS_KIND
Gibt die Arten von Adressen an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Felder
`ADDRESS_KIND_NATIVE`\
Eine native Adresse, die durch die [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) -Struktur dargestellt wird.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Eine nicht verwaltete Adresse relativ zu einem `this` `Me` -Zeiger (in Visual Basic), der durch die [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur dargestellt wird.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Eine nicht verwaltete physische Adresse, die durch die [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur dargestellt wird.

`ADDRESS_KIND_METHOD`\
Eine Methode einer Klasse, die durch die [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) -Struktur dargestellt wird.

`ADDRESS_KIND_FIELD`\
Ein Feld einer Klasse, das durch die [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur dargestellt wird.

`ADDRESS_KIND_LOCAL`\
Die Adresse ist für eine lokale Variable und wird durch die [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) -Struktur dargestellt.

`ADDRESS_KIND_PARAM`\
Eine Methode oder ein Funktionsparameter, der durch die [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur dargestellt wird.

`ADDRESS_KIND_ARRAYELEM`\
Ein Array Element, das durch die [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) -Struktur dargestellt wird.

`ADDRESS_KIND_RETVAL`\
Ein Rückgabewert, der durch die [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) -Struktur dargestellt wird.

## <a name="remarks"></a>Bemerkungen
Die [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) -Methode gibt die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur zurück, die eine Vereinigung möglicher Strukturen, die [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur enthält. Das `dwKind` -Feld der `DEBUG_ADDRESS_UNION` -Struktur enthält den `ADDRESS_KIND` Wert und beschreibt, wie das Union-Feld interpretiert wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
