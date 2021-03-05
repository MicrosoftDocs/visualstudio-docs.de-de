---
description: Gibt die Kriterien für den Vergleich von zwei Speicher Kontexten an.
title: CONTEXT_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70f4621eaad5e494684e6c227959e13566a22eba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170782"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Gibt die Kriterien für den Vergleich von zwei Speicher Kontexten an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Felder
`CONTEXT_EQUAL`\
Suchen Sie den ersten Speicher Kontext in der Liste, der gleich dem Zielspeicher Kontext ist.

`CONTEXT_LESS_THAN`\
Suchen Sie den ersten Speicher Kontext in der Liste, der kleiner ist als der Zielspeicher Kontext.

`CONTEXT_GREATER_THAN`\
Suchen Sie den ersten Speicher Kontext in der Liste, der größer ist als der Zielspeicher Kontext.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Suchen Sie den ersten Speicher Kontext in der Liste, der kleiner oder gleich dem Zielspeicher Kontext ist.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Suchen Sie den ersten Speicher Kontext in der Liste, der größer oder gleich dem Zielspeicher Kontext ist.

`CONTEXT_SAME_SCOPE`\
Suchen Sie den ersten Speicher Kontext in der Liste, der sich im gleichen Bereich wie der Zielspeicher Kontext befindet.

`CONTEXT_SAME_FUNCTION`\
Suchen Sie den ersten Speicher Kontext in der Liste, der sich in derselben Funktion wie der Zielspeicher Bereich befindet.

`CONTEXT_SAME_MODULE`\
Suchen Sie den ersten Speicher Kontext in der Liste, der sich im selben Modul wie der Zielspeicher Kontext befindet.

`CONTEXT_SAME_PROCESS`\
Suchen Sie den ersten Speicher Kontext in der Liste, der sich im gleichen Prozess wie der Zielspeicher Kontext befindet.

## <a name="remarks"></a>Bemerkungen
Als Argument an die [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) -Methode übergebenen.

Diese Werte werden verwendet, um den ersten Speicher Kontext in einer Liste zu suchen, die die angegebenen Vergleichskriterien erfüllt. Einem Speicher Kontext wird eine Liste der Speicher Kontexte zugewiesen, mit denen sich die Methode über die-Methode vergleichen kann `IDebugMemoryContext2::Compare` . Der erste Speicher Kontext in der Liste, für den der Vergleichs Operator ist, `true` wird zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
