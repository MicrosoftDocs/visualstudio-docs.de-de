---
title: IDebugExceptionEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c09b81a6a3eb56734e7d3a95dc5d1a8d1717fba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933114"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Die Debug-Engine (de) sendet diese Schnittstelle an den Sitzungs-Debug-Manager (SDM), wenn im aktuell ausgeführten Programm eine Ausnahme ausgelöst wird.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um zu melden, dass eine Ausnahme in dem Programm aufgetreten ist, das gedeppt wird. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, um eine Ausnahme zu melden. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugExceptionEvent2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ruft ausführliche Informationen zu der Ausnahme ab, die dieses Ereignis ausgelöst hat.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ruft eine lesbare Beschreibung der Ausnahme ab, die ausgelöst wird, die dieses Ereignis ausgelöst hat.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Bestimmt, ob die Debug-Engine (de) die Option unterstützt, diese Ausnahme an das Programm zu übergeben, das beim Fortsetzen der Ausführung debuggt wird.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Gibt an, ob die Ausnahme an das Programm weitergegeben werden soll, das beim Fortsetzen der Ausführung deentschlgt wird, oder, wenn die Ausnahme verworfen werden soll.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Bemerkungen
 Vor dem Senden des Ereignisses prüft de, ob dieses Ausnahme Ereignis durch einen vorherigen Aufrufen von [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)als erste Chance oder zweite Chance bezeichnet wurde. Wenn es sich um eine Ausnahme der ersten Chance `IDebugExceptionEvent2` handelt, wird das Ereignis an die SDM gesendet. Andernfalls gibt die de der Anwendung die Möglichkeit, die Ausnahme zu behandeln. Wenn kein Ausnahmehandler bereitgestellt wird und die Ausnahme als Ausnahme der zweiten Chance festgelegt wurde, `IDebugExceptionEvent2` wird das Ereignis an die SDM gesendet. Andernfalls wird die Ausführung des Programms von de fortgesetzt, und das Betriebssystem oder die Laufzeit behandelt die Ausnahme.

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
