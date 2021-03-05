---
description: Eine-Struktur, die eine Liste der GUID enthält.
title: CONST_GUID_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3caa4518872abbb2164e523b30679621d2bf319c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170808"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
Eine-Struktur, die eine Liste von `GUID` s enthält.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Members
`dwCount`\
Anzahl von `GUID` s im `Members` Array.

`Members`\
Array von `GUID` s.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [publishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) -Methode übermittelt und von der [getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) -Methode und der [watchforproviderevents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) -Methode zurückgegeben.

Der Besitzer einer Instanz dieser Struktur ist dafür verantwortlich, zugeordneten Arbeitsspeicher freizugeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
