---
description: Gibt an, wie ein Ausdruck analysiert wird.
title: Parameeflags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192e4de399540ce189bbf52cbb0f615b2b9bc855
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222145"
---
# <a name="parseflags"></a>PARSEFLAGS
Gibt an, wie ein Ausdruck analysiert wird.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Felder
 `PARSE_EXPRESSION`\
 Gibt an, dass der Ausdruck keine Anweisung ist.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Gibt an, dass der Ausdruck als Adresse analysiert (und später ausgewertet) werden soll.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Gibt an, dass der Ausdruck während der Entwurfszeit analysiert wird (d. h., wenn ein Designer geöffnet ist).

## <a name="remarks"></a>Bemerkungen
 Übergeben als Parameter an [die Methoden "](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) [Parametertext](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " und "Analyse".

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
