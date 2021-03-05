---
description: Beschreibt die gebundenen Haltepunkt Informationen für einen Code-Haltepunkt oder einen Daten Breakpoint.
title: BP_RESOLUTION_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9acdc85cd7ea3e8da239395e5db8c921936a98bd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162588"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Beschreibt die gebundenen Haltepunkt Informationen für einen Code-Haltepunkt oder einen Daten Breakpoint.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Members
`dwFields`\
Eine Auflistung von Flags aus den [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) Enumerationen, die angibt, welche Felder ausgefüllt werden.

`bpResLocation`\
Die [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) -Struktur, die die Position des Breakpoints im Code oder in den Daten angibt.

`pProgram`\
Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das die Anwendung darstellt, in der der Breakpoint-Fehler aufgetreten ist.

`pThread`\
Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem die Anwendung, die den Breakpoint-Fehler enthält, ausgeführt wird.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von [getresolutioninfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
