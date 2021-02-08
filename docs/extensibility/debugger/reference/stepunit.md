---
title: Stepunit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f42c6af308770132343e18b95a9f839717f6d401
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840092"
---
# <a name="stepunit"></a>STEPUNIT
Gibt die Schritt Einheit für die schrittweise Angabe an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Felder
 `STEP_STATEMENT`\
 Steps by-Anweisung.

 `STEP_LINE`\
 Schritte nach Zeile.

 `STEP_INSTRUCTION`\
 Schritte nach Anweisung.

## <a name="remarks"></a>Bemerkungen
 Wird als Argument an die [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) -Methode übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)
