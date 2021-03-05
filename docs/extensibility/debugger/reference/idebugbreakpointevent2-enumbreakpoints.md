---
description: Erstellt einen Enumerator für alle Breakpoints, die an der aktuellen Codeposition ausgelöst werden.
title: 'IDebugBreakpointEvent2:: enumbreakpoints | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bccb263fbdfebe1a83dab5f2ce5f570338b6d2e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143352"
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Erstellt einen Enumerator für alle Breakpoints, die an der aktuellen Codeposition ausgelöst werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumBreakpoints(
  IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBreakpoints(
  out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) -Objekt zurück, das alle Breakpoints auflistet, die dem aktuellen Code Speicherort zugeordnet sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nicht alle Haltepunkte an einem bestimmten Speicherort können zu einem bestimmten Zeitpunkt ausgelöst werden (ein Haltepunkt mit einer Bedingung wird z. b. erst ausgelöst, wenn diese Bedingung erfüllt ist).

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
