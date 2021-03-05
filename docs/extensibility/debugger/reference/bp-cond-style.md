---
description: Gibt den Haltepunkt-Bedingungs Stil für ausstehende und gebundene Haltepunkte an.
title: BP_COND_STYLE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c23549d1553902c00048f946d2711c497fbe2322
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144480"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Gibt den Haltepunkt-Bedingungs Stil für ausstehende und gebundene Haltepunkte an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Felder
`BP_COND_NONE`\
Löst den Haltepunkt aus, wenn die Position des Breakpoints erreicht ist. Es wurde keine breakpointbedingung angegeben.

`BP_COND_WHEN_TRUE`\
Löst den Haltepunkt nur aus, wenn der bedingte Ausdruck, der dem Breakpoint zugeordnet ist, zu ausgewertet wird `true` .

`BP_COND_WHEN_CHANGED`\
Löst den Breakpoint nur aus, wenn sich der Wert des bedingten Ausdrucks, der dem Breakpoint zugeordnet ist, von der vorherigen Auswertung geändert hat.

## <a name="remarks"></a>Bemerkungen
Wird für den `styleCondition` Member der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
