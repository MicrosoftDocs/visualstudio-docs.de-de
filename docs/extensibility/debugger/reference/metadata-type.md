---
title: METADATA_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d41716dcbc1aefba52f6507bb624973f36025af0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938731"
---
# <a name="metadata_type"></a>METADATA_TYPE
Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parameter
 `ulAppDomainID`\
 Die ID der Anwendung, von der das Symbol stammt. Hiermit wird eine Instanz der Anwendung eindeutig identifiziert.

 `guidModule`\
 Der GUID des Moduls, das dieses Feld enthält.

 `tokClass`\
 Die Metadatentoken-ID dieses Typs.

 [C++] `_mdToken` ist eine `typedef` für ein 32-Bit- `int` .

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) -Struktur angezeigt, wenn das- `dwKind` Feld der- `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_METADATA` (ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration).

 Der `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Ausführliche Informationen zum Interpretieren der oberen Bits der metadatentokenkennung finden Sie in der- `CorTokenType` Enumeration in der Datei "corhdr. h" im .NET Framework SDK.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
