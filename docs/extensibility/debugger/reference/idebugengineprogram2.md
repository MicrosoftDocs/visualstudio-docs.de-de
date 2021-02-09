---
title: IDebugEngineProgram2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f630614dbe49e87b5a9905ceabbf717269c98ea2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892605"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Diese Schnittstelle bietet Multithread-Debugunterstützung.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer Debug-Engine implementiert, um das gleichzeitige Debuggen mehrerer Threads Diese Schnittstelle wird auf demselben Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von einer `IDebugProgram2` Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEngineProgram2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die in diesem Programm ausgeführt werden.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Überwacht, dass die Ausführung auf dem angegebenen Thread erfolgt (oder die Ausführung der Ausführung beendet wird).|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Ermöglicht (oder verweigert) die Ausdrucks Auswertung auf dem angegebenen Thread, auch wenn das Programm beendet wird.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle als Reaktion auf ein [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis auf und legt den Status "nach Thread Schritt überwachen" und "Überwachung der Ausdrucks Auswertung auf Thread" des Programms fest. " [Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " wird immer dann aufgerufen, wenn das Programm beendet werden soll. Diese Methode gibt dem Programm die Möglichkeit, alle Threads zu beenden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
