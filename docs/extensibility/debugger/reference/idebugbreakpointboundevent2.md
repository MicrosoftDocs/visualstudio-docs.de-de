---
description: Diese Schnittstelle weist den sitzungsdebug-Manager (SDM) darauf hin, dass ein ausstehender Haltepunkt erfolgreich an ein geladenes Programm gebunden wurde.
title: IDebugBreakpointBoundEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3969010a59e66a8931c7f99d337b6f2ad373ccc4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143570"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Diese Schnittstelle weist den sitzungsdebug-Manager (SDM) darauf hin, dass ein ausstehender Haltepunkt erfolgreich an ein geladenes Programm gebunden wurde.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das von de erstellt und sendet dieses Ereignis Objekt, wenn ein ausstehender Haltepunkt erfolgreich an das gedestete Programm gebunden wird. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBreakpointBoundEvent2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, der gebunden wird.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Erstellt einen Enumerator von Breakpoints, die an dieses Ereignis gebunden wurden.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Breakpoint gebunden ist, wird ein Ereignis an die SDM gesendet. Wenn der Breakpoint nicht gebunden werden kann, wird ein [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gesendet. Andernfalls wird eine `IDebugBreakpointBoundEvent2` gesendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
