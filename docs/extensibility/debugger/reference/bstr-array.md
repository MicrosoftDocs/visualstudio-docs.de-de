---
description: Eine-Struktur, die ein Array von Zeichen folgen beschreibt.
title: BSTR_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5fb882bb31f6fd525d00dc134e042e9bce9398f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170971"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Eine-Struktur, die ein Array von Zeichen folgen beschreibt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Members
`dwCount`\
Anzahl der Zeichen folgen im `Members` Array.

`Members`\
Array von Zeichen folgen.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) -Methode zurückgegeben.

 [Nur C++] Jede einzelne Zeichenfolge muss mit freigegeben werden `SysFreeString` , und das `Members` Array muss mit freigegeben werden `CoTaskMemFree` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
