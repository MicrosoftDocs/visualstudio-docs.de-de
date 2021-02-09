---
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
ms.openlocfilehash: d16eb78cdb6c6b9e665dda8410f46d4cf61ee69a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882211"
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

## <a name="members"></a>Member
`dwCount`\
Anzahl der Zeichen folgen im `Members` Array.

`Members`\
Array von Zeichen folgen.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) -Methode zurückgegeben.

 [Nur C++] Jede einzelne Zeichenfolge muss mit freigegeben werden `SysFreeString` , und das `Members` Array muss mit freigegeben werden `CoTaskMemFree` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
