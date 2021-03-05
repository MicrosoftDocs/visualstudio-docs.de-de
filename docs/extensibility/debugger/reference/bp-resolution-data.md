---
description: Beschreibt das Ergebnis der Bindung eines Daten Breakpoints.
title: BP_RESOLUTION_DATA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d33f05036965e500a007b97e7575a5c0d788158
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162614"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Beschreibt das Ergebnis der Bindung eines Daten Breakpoints.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Members
`bstrDataExpr`\
Der Daten Ausdruck, der gebunden wurde.

`bstrFunc`\
Der Name der Funktion, an die der Daten Breakpoint gebunden ist (sofern vorhanden).

`bstrImage`\
Der Name des Moduls (z. b. MyModule.dll), an das der Daten Breakpoint gebunden ist.

`dwFlags`\
Ein Wert aus der [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) -Enumeration, die beschreibt, wie der Daten Haltepunkt implementiert wird.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Struktur, der wiederum ein Member der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur ist, die von der [getresolutioninfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) -Methode zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
