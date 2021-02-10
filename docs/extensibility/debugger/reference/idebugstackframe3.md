---
title: IDebugStackFrame3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5511624fb69015351d8cc37d6b27ad142a5956d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961182"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Diese Schnittstelle erweitert [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , um abgefangene Ausnahmen zu verarbeiten.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle implementiert, um abgefangene Ausnahmen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugStackFrame2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)geerbt werden, werden `IDebugStackFrame3` die folgenden Methoden von verfügbar gemacht.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Behandelt eine Ausnahme für den aktuellen Stapel Rahmen vor jeder regulären Ausnahmebehandlung.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Gibt einen Code Kontext zurück, wenn eine Stapel Entladung auftreten würde.|

## <a name="remarks"></a>Bemerkungen
 Eine abgefangene Ausnahme bedeutet, dass ein Debugger eine Ausnahme verarbeiten kann, bevor alle normalen Routinen zur Ausnahmebehandlung von der Laufzeit aufgerufen werden. Das Abfangen einer Ausnahme bedeutet im Wesentlichen, dass die Laufzeit vorgibt, dass ein Ausnahmehandler vorhanden ist, auch wenn dies nicht der Fall ist.

- [Intercepteption TException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) wird während aller normalen Ausnahmen Rückruf Ereignisse aufgerufen (die einzige Ausnahme besteht darin, dass Sie Code im gemischten Modus Debuggen (verwalteter und nicht verwalteter Code). in diesem Fall kann die Ausnahme während des Rückrufs der letzten Chance nicht abgefangen werden. Wenn die de nicht implementiert `IDebugStackFrame3` , oder die de einen Fehler von IDebugStackFrame3:: (z. b.) zurückgibt `InterceptCurrentException` `E_NOTIMPL` , wird die Ausnahme vom Debugger normal behandelt.

 Durch das Abfangen einer Ausnahme kann der Debugger es dem Benutzer ermöglichen, Änderungen am Zustand des debuggten Programms vorzunehmen und die Ausführung dann an dem Punkt fortzusetzen, an dem die Ausnahme ausgelöst wurde.

> [!NOTE]
> Abgefangene Ausnahmen sind nur in verwaltetem Code zulässig, d. h. in einem Programm, das unter der Common Language Runtime (CLR) ausgeführt wird.

 Eine Debug-Engine gibt an, dass Sie das Abfangen von Ausnahmen unterstützt, indem "metricexceptions" zur Laufzeit mithilfe der-Funktion auf den Wert 1 festgelegt wird `SetMetric` . Weitere Informationen finden Sie unter [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
