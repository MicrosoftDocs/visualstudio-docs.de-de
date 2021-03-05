---
description: Diese Schnittstelle stellt einen Thread dar, der in einem Programm ausgeführt wird.
title: IDebugThread2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8b09aa546e4711b1c11623a3596ba0e385b2a14
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164421"
---
# <a name="idebugthread2"></a>IDebugThread2
Diese Schnittstelle stellt einen Thread dar, der in einem Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um einen Ausführungs Thread in einem einzelnen Programm darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) auf, um diese Schnittstelle abzurufen, die den momentan aktiven Thread darstellt.

 Diese Schnittstelle wird auch zum Erstellen einer breakpointanforderung verwendet (siehe [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Diese Schnittstelle wird auch zurückgegeben, wenn ein gebundener oder fehlerender Haltepunkt aufgelöst wird (siehe [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) und [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugThread2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Ruft eine Liste der Stapel Rahmen für diesen Thread ab.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ruft den Namen des Threads ab.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Legt den Namen des Threads fest.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ruft das Programm ab, in dem ein Thread ausgeführt wird.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Bestimmt, ob die nächste Anweisung auf den angegebenen Stapel Rahmen und Code Kontext festgelegt werden kann.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Legt die nächste Anweisung auf den angegebenen Stapel Rahmen und Code Kontext fest.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ruft den System Thread Bezeichner ab.|
|[Angehalten](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Hält einen Thread an.|
|[Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Setzt einen Thread fort.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ruft Eigenschaften ab, die einen Thread beschreiben.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ruft den logischen Thread ab, der diesem physischen Thread zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Da ein einzelner physischer Thread in mehreren Programmen ausgeführt werden kann, kann mehr als ein `IDebugThread2` Programm aus mehreren Programmen denselben physischen Thread darstellen.

 Wenn ein Breakpoint oder eine Ausnahme auftritt, wird vom aufrufenden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)ein Ereignis gesendet. Eines der Argumente für diese Methode ist eine `IDebugThread2` Schnittstelle, die den aktuellen Thread darstellt. [Enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) wird zum Abrufen der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle für den aktuellen Stapel Rahmen verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
