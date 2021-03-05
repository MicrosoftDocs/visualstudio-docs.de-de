---
description: Diese Schnittstelle stellt einen Haltepunkt dar, der an einen Code Speicherort gebunden ist.
title: IDebugBoundBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2726a2422c49335d9c95e7d500381ad1fdc0108
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167476"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt dar, der an einen Code Speicherort gebunden ist.

## <a name="syntax"></a>Syntax

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Durch einen [Bindungs Bindungs](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) Befehl wird diese Schnittstelle erstellt. Aufrufe von " [getbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) " und " [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) " können diese Schnittstelle ebenfalls abrufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBoundBreakpoint2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Breakpoint ab, von dem der angegebene gebundene Breakpoint erstellt wurde.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand dieses gebundenen halte Punkts ab.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ruft die aktuelle Treffer Anzahl für diesen gebundenen Haltepunkt ab.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die breakpointauflösung ab, die diesen Haltepunkt beschreibt.|
|[Aktivieren](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert den Breakpoint.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Legt die Treffer Anzahl für diesen gebundenen Haltepunkt fest.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Legt die diesem gebundenen Haltepunkt zugeordnete Bedingung fest oder ändert diese.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Legt die mit diesem gebundenen Haltepunkt verknüpfte Durchlauf Anzahl fest oder ändert diese.|
|[Löschen](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht den Haltepunkt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Zwick](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
