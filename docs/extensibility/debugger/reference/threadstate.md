---
description: Gibt den Status des Threads an.
title: Thread State | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c44eaf3b5ab8d3515b2c3e2128e8ac9562492e
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225255"
---
# <a name="threadstate"></a>THREADSTATE
Gibt den Status des Threads an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Felder
 `THREADSTATE_RUNNING`\
 Gibt an, dass der Thread ausgeführt wird.

 `THREADSTATE_STOPPED`\
 Gibt an, dass der Thread aufgrund eines Breakpoints angehalten wird.

 `THREADSTATE_FRESH`\
 Gibt an, dass der Thread erstellt, aber noch nicht ausgeführt wird.

 `THREADSTATE_DEAD`\
 Gibt an, dass der Thread nicht aktiv ist.

 `THREADSTATE_FROZEN`\
 Gibt an, dass der Thread eingefroren ist (es kann keine Ausführung ausgeführt werden).

## <a name="remarks"></a>Bemerkungen
 Wird für das- `dwThreadState` Feld der [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
