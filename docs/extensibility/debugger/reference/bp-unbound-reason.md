---
title: BP_UNBOUND_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c4750b4d1a9c1f972c0445dfcf3ea2f4fa5be328
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842654"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Gibt den Grund für die Bindung eines Breakpoints an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Felder
`BPUR_UNKNOWN`\
Der Grund ist unbekannt.

`BPUR_CODE_UNLOADED`\
Der Code, der den Breakpoint enthält, wurde entladen.

`BPUR_BREAKPOINT_REBIND`\
Der Breakpoint wurde an einen anderen Speicherort wieder gebunden. Dies kann nach dem Bearbeiten und Fortfahren erfolgen, wenn der Breakpoint verschoben wird, oder wenn der Breakpoint an eine Datei mit einem Pfad gebunden ist, der nicht mehr gültig ist.

`BPUR_ BREAKPOINT_ERROR`\
Der Haltepunkt wird als fehlerhaft festgelegt, nachdem er gebunden wurde. Dies geschieht bei verwalteten Haltepunkten, deren Bedingungen nicht mehr gültig sind.

## <a name="remarks"></a>Bemerkungen
Wird von der [geverrat](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
