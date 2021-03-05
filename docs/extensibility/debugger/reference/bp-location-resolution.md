---
description: Beschreibt die Auflösung eines Breakpoints an einer bestimmten Position.
title: BP_LOCATION_RESOLUTION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 80ed7f4f0206542e5f6a4289aba1d833eef5937a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144220"
---
# <a name="bp_location_resolution"></a>BP_LOCATION_RESOLUTION
Beschreibt die Auflösung eines Breakpoints an einer bestimmten Position.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_RESOLUTION {
    IDebugBreakpointResolution2* pResolution;
} BP_LOCATION_RESOLUTION;
```

## <a name="members"></a>Members
`pResolution`\
Das [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) -Objekt, das den Typ des Breakpoints und dessen Auflösungsinformationen bestimmt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
