---
description: Dient zum Festlegen von Code Breakpoints basierend auf einer Zeichenfolge, die der Benutzer aus der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) eingeben kann.
title: BP_LOCATION_CODE_STRING | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9508a4a83894757fb47e35d8db7334bfb144ff59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144376"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Dient zum Festlegen von Code Breakpoints basierend auf einer Zeichenfolge, die der Benutzer aus der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) eingeben kann.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Members
`bstrContext`\
Der Kontext des Breakpoints innerhalb des Codes, in der Regel ein Methoden-oder Funktionsname, wie er in einer-aufrufsstapel angezeigt wird.

`bstrCodeExpr`\
Die Zeichenfolge, die der Benutzer eingibt, um den Code Breakpoint zu beschreiben.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
