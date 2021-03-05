---
description: Wird verwendet, um Daten Breakpoints festzulegen, die auf einer Zeichenfolge basieren, die der Benutzer aus der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) eingeben kann.
title: BP_LOCATION_DATA_STRING | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 1e4a250843ebbb6ab7680040e3aa296699e184ee
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144350"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Wird verwendet, um Daten Breakpoints festzulegen, die auf einer Zeichenfolge basieren, die der Benutzer aus der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) eingeben kann.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Members
`pThread`\
Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem der Breakpoint auftritt.

`bstrContext`\
Der Kontext des Breakpoints innerhalb des Codes, in der Regel ein Methoden-oder Funktionsname, wie er in einer-aufrufsstapel angezeigt wird.

`bstrDataExpr`\
Die Daten Zeichenfolge, die der Benutzer zum Festlegen des Breakpoints eingibt.

`dwNumElements`\
Die Anzahl der Elemente in der Daten Zeichenfolge, in der der Breakpoint auftritt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
