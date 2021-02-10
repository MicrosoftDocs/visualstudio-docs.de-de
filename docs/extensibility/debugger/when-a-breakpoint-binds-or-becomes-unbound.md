---
title: Wenn ein Breakpoint gebunden wird oder ungebunden wird | Microsoft-Dokumentation
description: Erfahren Sie mehr über ungebundene Breakpoints. Wenn ein Haltepunkt zum Zeitpunkt der Erstellung eines Aufrufes nicht gebunden werden kann, unterscheiden sich die Bindungs Zeit und die Erstellungszeit des Breakpoints.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97ac7dc9afbd3b740c95a7e76a30836e938eaeaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968501"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Wenn ein Breakpoint gebunden wird oder die Bindung aufgehoben wird
Wenn ein Breakpoint nicht gebunden werden kann, wenn ein Aufruf an die [IDebugPendingBreakpoint2:: canbind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) -Methode erfolgt, unterscheiden sich die Bindungs Zeit und die Erstellungszeit des Breakpoints.

## <a name="methods-called"></a>Aufgerufene Methoden
 Der Sitzungs-Debug-Manager (SDM) Ruft die folgenden Methoden auf:

1. [IDebugEngine2:: kreateperdingbreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE gibt ein [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)-Wert zurück.

2. [IDebugPendingBreakpoint2:: enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Die [IDebugPendingBreakpoint2:: Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) -Methode und gibt S_OK zurück. Der de sendet eine [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) oder [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [IDebugBreakpointBoundEvent2:: getpdingbreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) -und [IDebugBreakpointBoundEvent2:: enumboundbreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) -Methoden, um zu überprüfen und die gebundenen Haltepunkte zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
