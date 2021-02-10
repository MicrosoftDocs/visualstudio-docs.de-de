---
title: LAUNCH_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2457f6e18af75a515c0e27889ffecea521670db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962092"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
Gibt die debugstartflags an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="fields"></a>Felder
`LAUNCH_DEBUG`\
Hiermit wird der Prozess zum Debuggen gestartet.

`LAUNCH_NODEBUG`\
Starten des Prozesses, ohne ihn zu debuggen.

`LAUNCH_ENABLE_ENC`\
veraltet, nicht verwenden.

`LAUNCH_MERGE_ENV`\
Der Prozess wird gestartet, und die Umgebung wird mit dem Start Host zusammengeführt.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden als Argument an die [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) alten-Methode übermittelt.

Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
