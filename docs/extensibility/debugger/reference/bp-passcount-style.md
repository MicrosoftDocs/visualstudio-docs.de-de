---
description: Gibt die Bedingung an, die der Breakpoint-Durchlauf Anzahl zugeordnet ist, die bewirkt, dass der Breakpoint ausgelöst wird.
title: BP_PASSCOUNT_STYLE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e216b61d6fed41571baa7f68201d96f84532fc3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144168"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Gibt die Bedingung an, die der Breakpoint-Durchlauf Anzahl zugeordnet ist, die bewirkt, dass der Breakpoint ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Felder
`BP_PASSCOUNT_NONE`\
Gibt den Wert für die Anzahl der Haltepunkt übergebenen an

`BP_PASSCOUNT_EQUAL`\
Legt den Wert für den Haltepunkt Durchlauf auf gleich fest. Der Breakpoint wird ausgelöst, wenn die Anzahl der Treffer des Breakpoints der Durchlauf Anzahl entspricht.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Legt den Wert für den Haltepunkt Durchlauf auf gleich oder größer fest. Der Haltepunkt wird ausgelöst, wenn die Anzahl der Treffer des Breakpoints größer oder gleich der Durchlauf Anzahl ist.

`BP_PASSCOUNT_MOD`\
Gibt eine Modulo-Anzahl an. Wenn beispielsweise die Anzahl der Pass-Werte vom Typ `BP_PASSCOUNT_MOD` und der Wert für die Durchlauf Anzahl 4 ist, wird der Breakpoint jedes Mal ausgelöst, wenn die Treffer Anzahl ein Vielfaches von 4 ist.

## <a name="remarks"></a>Bemerkungen
Wird für den `stylePassCount` Member der [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur verwendet, der wiederum ein Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen ist.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
