---
title: Stepkind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4c87a2c221149f8478a083d1efea6e9edfb542d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965472"
---
# <a name="stepkind"></a>STEPKIND
Gibt die schrittart für die schrittweise Angabe an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Felder
 `STEP_INTO`\
 Führt einen Schritt in eine Funktion aus.

 `STEP_OVER`\
 Schritte für eine Funktion.

 `STEP_OUT`\
 Führt eine Funktion aus.

 `STEP_BACKWARDS`\
 Führt einen rückwärts Schritt in eine Funktion aus.

## <a name="remarks"></a>Bemerkungen
 Wird als Argument an die [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) -Methode übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)
