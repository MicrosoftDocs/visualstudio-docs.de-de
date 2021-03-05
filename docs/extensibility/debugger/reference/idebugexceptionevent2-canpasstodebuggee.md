---
description: Bestimmt, ob die Debug-Engine (de) die Option unterstützt, diese Ausnahme an das Programm zu übergeben, das beim Fortsetzen der Ausführung debuggt wird.
title: 'IDebugExceptionEvent2:: canpasstodebug | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152883"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Bestimmt, ob die Debug-Engine (de) die Option unterstützt, diese Ausnahme an das Programm zu übergeben, das beim Fortsetzen der Ausführung debuggt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Rückgabewert
 Gibt entweder `S_OK` (die Ausnahme kann an das Programm weitergegeben werden) oder `S_FALSE` (die Ausnahme kann nicht weitergegeben werden) zurück.

## <a name="remarks"></a>Bemerkungen
 Die de muss über eine Standardaktion zum übergeben an die zu debuggende Komponente verfügen. Die IDE empfängt möglicherweise das [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) -Ereignis und ruft die [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) -Methode auf, ohne die-Methode aufzurufen `CanPassToDebuggee` . Daher sollte die de über einen Standardfall zum übergeben der Ausnahme verfügen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
