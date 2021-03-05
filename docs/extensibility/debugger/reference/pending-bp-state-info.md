---
description: Enthält Informationen zum Zustand eines Breakpoints, der für die Bindung an einen Code Speicherort bereit ist.
title: PENDING_BP_STATE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edd4bbdde1c241d90329343be1fd5570129c675a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223926"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Enthält Informationen zum Zustand eines Breakpoints, der für die Bindung an einen Code Speicherort bereit ist.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Members
 `state`\
 Ein Wert aus der [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) Enumeration, der den Status des ausstehenden halte Punkts angibt.

 `flags`\
 Eine Kombination von Flags aus der [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) -Enumeration, die angibt, ob der Breakpoint virtualisiert ist.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) -Methode übermittelt, wo Sie ausgefüllt ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
