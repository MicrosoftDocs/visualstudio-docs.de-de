---
description: Beschreibt die Anzahl und die Bedingungen, auf die ein bedingter Breakpoint ausgelöst wird.
title: BP_PASSCOUNT | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c1e44ede0f39b3d1b33967311365508da6a701d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144155"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Beschreibt die Anzahl und die Bedingungen, auf die ein bedingter Breakpoint ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Members
`dwPassCount`\
Gibt an, wie oft über den Haltepunkt übergeben werden soll, bevor es ausgelöst wird.

`stylePassCount`\
Ein Wert aus der [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Enumeration, der den Stil der Breakpoint-Durchlauf Anzahl angibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -Struktur.

Diese Struktur wird auch als Parameter an die[setpasscount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) -Methode und die[setpasscount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) -Methode übergeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
