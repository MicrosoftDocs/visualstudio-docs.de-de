---
description: Beschreibt die Eigenschaften eines Prozesses oder legt diese fest.
title: PROCESS_INFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e192a51c2c371754778ecbe697d280d1b254f224
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225330"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Beschreibt die Eigenschaften eines Prozesses oder legt diese fest.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Felder

`PIFLAG_SYSTEM_PROCESS`\
Gibt an, dass der Prozess ein System Prozess ist.

`PIFLAG_DEBUGGER_ATTACHED`\
Gibt an, dass der Prozess von einem Debugger debuggt wird. Möglicherweise handelt es sich [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] um einen Debugger, oder es handelt sich um einen anderen Debugger, z. b. WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Gibt an, dass der Prozess beendet wurde. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben ist. Verfügbar in Visual Studio 2005 und höher.

`PIFLAG_PROCESS_RUNNING`\
Gibt an, dass der Prozess ausgeführt wird. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben ist. Verfügbar in Visual Studio 2005 und höher.

## <a name="remarks"></a>Bemerkungen

Wird für den `Flags` Member der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) -Struktur verwendet.

Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen

Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch

- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
