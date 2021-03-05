---
description: Gibt an, dass ein gebundener Haltepunkt vorhanden ist, und gibt außerdem an, ob er aktiviert ist.
title: BP_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ae225a7eeb782257a716c48c1882d78ad150e7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168334"
---
# <a name="bp_state"></a>BP_STATE
Gibt an, dass ein gebundener Haltepunkt vorhanden ist, und gibt außerdem an, ob er aktiviert ist.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Felder
`BPS_NONE`\
Gibt an, dass kein Haltepunkt vorhanden ist.

`BPS_DELETED`\
Gibt an, dass der Breakpoint gelöscht wurde.

`BPS_DISABLED`\
Gibt an, dass der Breakpoint deaktiviert ist.

`BPS_ENABLED`\
Gibt an, dass der Breakpoint aktiviert ist.

## <a name="remarks"></a>Bemerkungen
Wird von der [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) -Methode zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
