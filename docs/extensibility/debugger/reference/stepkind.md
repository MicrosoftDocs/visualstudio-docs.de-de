---
description: Gibt die schrittart für die schrittweise Angabe an.
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
ms.openlocfilehash: a9cb230eac9e8851437614a590615ad2402923f6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225291"
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
