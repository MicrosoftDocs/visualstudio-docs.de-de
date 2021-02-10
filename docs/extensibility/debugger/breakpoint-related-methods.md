---
title: Breakpoint-Related Methoden | Microsoft-Dokumentation
description: Das Visual Studio-debuggen unterstützt gebundene Haltepunkte, die erfolgreich an einen Speicherort im Code gebunden sind, und ausstehende Haltepunkte, die noch nicht gebunden sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c20a92e847f120850d7cbd424cc073018903911d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930823"
---
# <a name="breakpoint-related-methods"></a>Methoden im Zusammenhang mit Breakpoints
Eine Debug-Engine (de) muss die Einstellung von Haltepunkten unterstützen. Das Visual Studio-debuggen unterstützt die folgenden Typen von Breakpoints:

- Bound

     Über die Benutzeroberfläche angefordert und erfolgreich an einen angegebenen Code Speicherort gebunden

- Ausstehend

     Über die Benutzeroberfläche angefordert, aber noch nicht an tatsächliche Anweisungen gebunden

## <a name="discussion"></a>Diskussion
 Ein ausstehender Haltepunkt tritt beispielsweise auf, wenn die Anweisungen noch nicht geladen wurden. Wenn der Code geladen wird, versuchen ausstehende Haltepunkte, an dem vorgeschriebenen Speicherort an den Code zu binden, d. h., um unter brechungsanweisungen in den Code einzufügen. Ereignisse werden an den Sitzungs-Debug-Manager (SDM) gesendet, um eine erfolgreiche Bindung anzugeben oder um zu benachrichtigen, dass Bindungs Fehler aufgetreten sind.

 Ein ausstehender Haltepunkt verwaltet auch seine eigene interne Liste der entsprechenden gebundenen Haltepunkte. Ein ausstehender Haltepunkt kann dazu führen, dass viele Breakpoints in den Code eingefügt werden. Die Visual Studio-debuggingschnittstelle zeigt eine Strukturansicht von ausstehenden Breakpoints und deren zugehörigen gebundenen Haltepunkten an.

 Die Erstellung und Verwendung von ausstehenden Haltepunkten erfordert die Implementierung der [IDebugEngine2:: mpateperdingbreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) -Methode sowie der folgenden Methoden von [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstellen.

|Methode|Beschreibung|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob ein angegebener ausstehender Haltepunkt an einen Code Speicherort gebunden werden kann.|
|[Zwick](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet einen angegebenen ausstehenden Breakpoint an einen oder mehrere Code Speicherorte.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand eines ausstehenden halte Punkts ab.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Breakpoint-Anforderung ab, die zum Erstellen eines ausstehenden halte Punkts verwendet wird.|
|[Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Status eines ausstehenden Breakpoints um.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Haltepunkte auf, die von einem ausstehenden Haltepunkt gebunden sind.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Breakpunkte auf, die sich aus einem ausstehenden Haltepunkt ergeben.|
|[Löschen](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht einen ausstehenden Breakpoint und alle von ihm gebundenen Haltepunkte.|

 Um die gebundenen Haltepunkte und Fehler Haltepunkte aufzulisten, müssen Sie alle Methoden von [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) und von [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)implementieren.

 Ausstehende Breakpoints, die an einen Code Speicherort gebunden werden, erfordern die Implementierung der folgenden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) -Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Breakpoint ab, der einen Haltepunkt enthält.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand eines gebundenen halte Punkts ab.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die breakpointauflösung ab, die einen Breakpoint beschreibt.|
|[Aktivieren](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert einen Haltepunkt.|
|[Löschen](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht einen gebundenen Haltepunkt.|

 Auflösungs-und Anforderungs Informationen erfordern die Implementierung der folgenden [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) -Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Breakpoints ab, der durch eine Auflösung dargestellt wird.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur breakpointauflösung ab, die einen Breakpoint beschreiben.|

 Die Auflösung von Fehlern, die möglicherweise während der Bindung auftreten, erfordert die Implementierung der folgenden [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Breakpoint ab, der einen Fehler Haltepunkt enthält.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die breakpointfehlerauflösung ab, die einen Fehler-Breakpoint beschreibt.|

 Bei der Auflösung von Fehlern, die möglicherweise während der Bindung auftreten, sind auch die folgenden Methoden von [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)erforderlich.

|Methode|Beschreibung|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ eines Breakpoints ab.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Auflösungsinformationen eines Breakpoints ab.|

 Zum Anzeigen des Quellcodes an einem Breakpoint müssen Sie die Methoden von [IDebugStackFrame2:: getdocumentcontext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und/oder die Methoden von [IDebugStackFrame2:: getcodecontext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungs Steuerung und Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
