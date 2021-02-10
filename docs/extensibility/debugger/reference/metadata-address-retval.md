---
title: METADATA_ADDRESS_RETVAL | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec357bcc21cb3f7cd8f4f9eaa8318c4b0deb1d42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961897"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Diese Struktur stellt einen Rückgabewert einer Methode oder Funktion dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Member
 `tokMethod`\
 Die ID der Methode, für die dieser Rückgabewert gilt.

 `dwCorType`\
 Der Basistyp des Rückgabewerts. Dies ist ein Wert aus der- `CorElementType` Enumeration, die in der .NET Framework SDK-corhdr. h-Datei definiert ist.

 `dwSigSize`\
 Die Größe der Rückgabewert Signatur (wie in gespeichert `rgSig` ).

 `rgSig`\
 Ein Bytearray, das die Signatur des Rückgabewerts bildet.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, wenn das- `dwKind` Feld der- `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_RETVAL` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration).

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
