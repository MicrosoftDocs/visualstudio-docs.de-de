---
title: IDebugPendingBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6798d940bb186e6d685f22282e641eb2e690e48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877407"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt dar, der für die Bindung an einen Code Speicherort bereit ist.

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufrufen von " [anateperdingbreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) " erstellt einen ausstehenden Haltepunkt aus einer [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Schnittstelle. Ein [Bindungs BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt eine `IDebugBreakpoint2` Schnittstelle, die einen gebundenen Haltepunkt im Programm darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPendingBreakpoint2` .

|Methode|Beschreibung|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob dieser ausstehende Breakpoint an einen Code Speicherort gebunden werden kann.|
|[Zwick](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet diesen ausstehenden Breakpoint an einen oder mehrere Code Speicherorte.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand dieses ausstehenden halte Punkts ab.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Haltepunkt Anforderung ab, die zum Erstellen dieses ausstehenden Breakpoints verwendet wurde.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Schaltet den virtualisierten Zustand dieses ausstehenden Breakpoints um.|
|[Aktivieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand dieses ausstehenden Breakpoints um.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Legt die diesem ausstehenden Breakpoint zugeordnete Bedingung fest oder ändert diese.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Legt die mit diesem ausstehenden Haltepunkt verknüpfte Durchlauf Anzahl fest oder ändert diese.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Haltepunkte auf, die von diesem ausstehenden Haltepunkt gebunden sind.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Haltepunkte auf, die sich aus diesem ausstehenden Haltepunkt ergeben haben.|
|[Löschen](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht den ausstehenden Haltepunkt und alle von ihm gebundenen Haltepunkte.|

## <a name="remarks"></a>Bemerkungen
 `IDebugPendingBreakpoint2` kann als Anbieter aller notwendigen Informationen angesehen werden, die erforderlich sind, um einen Haltepunkt an Code zu binden, der auf ein oder mehrere Programme angewendet werden kann.

 Ein ausstehender Haltepunkt kann potenziell mehr als einen gebundenen Haltepunkt ergeben. Ein Haltepunkt in einer C++-Vorlage könnte z. b. einen gebundenen Haltepunkt für jede eindeutige Instanz dieser Vorlage erstellen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
