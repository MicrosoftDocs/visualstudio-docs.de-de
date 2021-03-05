---
description: Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.
title: BUILT_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd9f5984861b0f56e4a46b4f793a38bbb3bafa60
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170984"
---
# <a name="built_type"></a>BUILT_TYPE
Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Members
`ulAppDomainID`\
Die ID der Anwendung, von der das Symbol stammt. Hiermit wird eine Instanz der Anwendung eindeutig identifiziert.

`guidModule`\
Der GUID des Moduls, das dieses Feld enthält.

`pUnderlyingField`\
Ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das das zugrunde liegende Feld identifiziert, das diesem erstellten Feld zugeordnet ist.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) -Struktur angezeigt, wenn das- `dwKind` Feld der- `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_BUILT` (ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration).

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
