---
title: PENDING_BP_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12a1dfd610c86966aa22444924098051c4b50d21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934089"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Gibt den Status eines ausstehenden Breakpoints an (ein Haltepunkt, der noch nicht gebunden wurde).

## <a name="syntax"></a>Syntax

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Felder
 `PBPS_NONE`\
 Platzhalter für 0 (null). Dieser Wert wird niemals zurückgegeben.

 `PBPS_DELETED`\
 Gibt an, dass der ausstehende Breakpoint gelöscht wurde.

 `PBPS_DISABLED`\
 Gibt an, dass der ausstehende Breakpoint deaktiviert ist.

 `PBPS_ENABLED`\
 Gibt an, dass der ausstehende Breakpoint aktiviert ist.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie als `state` Member der [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Struktur.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
