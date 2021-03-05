---
description: Diese Struktur stellt eine Adresse dar, die relativ zu einem this-Zeiger ist (in Visual Basic).
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc3e72a536af25c3c62d953a0e5cfb75b5200c69
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223366"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Diese Struktur stellt eine Adresse dar, die relativ zu einem `this` Zeiger ist ( `Me` in Visual Basic).

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Members
 `dwOffset`\
 Byte Offset von einer Basis Position (z. b. Start einer Klasse Vtable).

 `dwBitOffset`\
 Offset in Bits von einer Basis Position (immer 0, es sei denn, es wird auf ein Bitfeld verwiesen).

 `dwBitLength`\
 Anzahl von Bits, die die Adresse darstellen (immer 0, sofern nicht auf ein Bitfeld verwiesen wird).

## <a name="remarks"></a>Bemerkungen
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, wenn das- `dwKind` Feld der- `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration).

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
