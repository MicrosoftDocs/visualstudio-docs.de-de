---
description: Beschreibt eine Methode oder einen Funktions Aufruf.
title: CODE_PATH | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ecdbbfdbcffbb8b1aa6246e2e99ef6eabfa1f19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170958"
---
# <a name="code_path"></a>CODE_PATH
Beschreibt eine Methode oder einen Funktions Aufruf.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Members
`bstrName`\
Der Name des Codepfade.

`pCode`\
Das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das angibt, an welcher Stelle im Code eine Funktion durchlaufen werden soll.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird verwendet, um Schritt-für-Schritt-Funktionen zu implementieren. [Enumcodepath](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) gibt alle Aufrufe von der aktuellen Position im debuggten Programm zurück. Diese Struktur stellt einen solchen-Rückruf dar.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
