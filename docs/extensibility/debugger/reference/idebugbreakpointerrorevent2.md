---
title: IDebugBreakpointErrorEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 033c997f3bd1038c2103a6c0ef3ad9ddbd74c249
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901863"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Diese Schnittstelle weist den sitzungsdebug-Manager (SDM) darauf hin, dass ein ausstehender Haltepunkt aufgrund einer Warnung oder eines Fehlers nicht an ein geladenes Programm gebunden werden konnte.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, wenn ein ausstehender Haltepunkt nicht an das zu Depende Programm gebunden werden kann. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBreakpointErrorEvent2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ruft die [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Schnittstelle ab, die die Warnung oder den Fehler beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Breakpoint gebunden ist, wird ein Ereignis an die SDM gesendet. Wenn der Haltepunkt nicht gebunden werden kann, `IDebugBreakpointErrorEvent2` wird eine gesendet, andernfalls wird ein [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gesendet.

 Wenn beispielsweise die dem ausstehenden Breakpoint zugeordnete Bedingung nicht analysiert oder ausgewertet werden kann, wird eine Warnung gesendet, dass der ausstehende Haltepunkt zu diesem Zeitpunkt nicht gebunden werden kann. Dies kann vorkommen, wenn der Code für den Breakpoint noch nicht geladen wurde.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
