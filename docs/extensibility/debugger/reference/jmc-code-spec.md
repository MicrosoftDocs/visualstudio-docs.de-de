---
title: JMC_CODE_SPEC | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0ca5fd553d94fdf866424b4cd0dc2b2a5fdb094
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962105"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Diese Struktur wird verwendet, um die JustMyCode-Informationen für ein Modul festzulegen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Member
`fIsUserCode`\
Ungleich NULL ( `TRUE` ), wenn das Modul als Benutzercode angesehen werden soll, andernfalls 0 (NULL `FALSE` ) (), wenn das Modul als externer Code behandelt werden soll und nicht deentschlgt werden soll.

`bstrModuleName`\
Der Name des fraglichen Moduls.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Liste solcher Strukturen an die [setjustmycodestate](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) -Methode übermittelt.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
