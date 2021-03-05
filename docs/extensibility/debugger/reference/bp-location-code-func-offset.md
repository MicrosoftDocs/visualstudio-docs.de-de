---
description: Beschreibt die Offset Position eines Breakpoints in einer Funktion im Code.
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 83a5a27601ab6d7498394d6723b86ad3e66aceb5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144363"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Beschreibt die Offset Position eines Breakpoints in einer Funktion im Code.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Members
`bstrContext`\
Der Kontext des Breakpoints, in der Regel ein Methoden-oder Funktionsname, wie er in einer-aufrufsstapel angezeigt wird.

`pFuncPos`\
Das [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) -Objekt, das den Namen der Funktion und die relative Position vom Anfang der Funktion beschreibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

Der `pFuncPos` Member gibt an, wo der Funktions Haltepunkt festgelegt werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
