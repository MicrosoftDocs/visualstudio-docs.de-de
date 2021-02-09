---
title: Binden von Haltepunkten | Microsoft-Dokumentation
description: Erfahren Sie, wie die IDE die Anforderung für einen Haltepunkt formuliert und die Debugsitzung anfordert, den Breakpoint zu erstellen, wenn ein Benutzer einen Haltepunkt festlegt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d7da8cfdb2b7995b77364e5a5de62667b13e52c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895010"
---
# <a name="bind-breakpoints"></a>Binden von Haltepunkten
Wenn der Benutzer einen Haltepunkt festlegt, vielleicht durch Drücken von **F9**, formuliert die IDE die Anforderung und fordert die Debugsitzung auf, den Haltepunkt zu erstellen.

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen
 Das Festlegen eines Breakpoints ist ein zweistufiger Prozess, da der vom Haltepunkt betroffene Code oder die Daten möglicherweise noch nicht verfügbar sind. Zuerst muss der Haltepunkt beschrieben werden, und anschließend muss er wie folgt an diesen Code oder diese Daten gebunden werden, wenn der Code oder die Daten verfügbar sind:

1. Der Haltepunkt wird von den relevanten Debug-engines (des) angefordert, und dann wird der Breakpoint an den Code oder die Daten gebunden, sobald er verfügbar wird.

2. Die breakpointanforderung wird an die Debugsitzung gesendet, die Sie an alle relevanten des sendet. Alle de, die sich für die Verarbeitung des Breakpoints entscheiden, erstellen einen entsprechenden ausstehenden Breakpoint.

3. Die Debugsitzung sammelt die ausstehenden Breakpoints und sendet Sie zurück an das Debugpaket (die Debugkomponente von Visual Studio).

4. Mit dem Debugpaket wird die Debugsitzung aufgefordert, den ausstehenden Haltepunkt an den Code oder die Daten zu binden. Die Debugsitzung sendet diese Anforderung an alle relevanten des.

5. Wenn die de in der Lage ist, den Breakpoint zu binden, sendet Sie ein Haltepunkt gebundenes Ereignis zurück an die Debugsitzung. Wenn dies nicht der Fall ist, wird stattdessen ein breakpointfehlerereignis gesendet.

## <a name="pending-breakpoints"></a>Ausstehende Breakpoints
 Ein ausstehender Haltepunkt kann an mehrere Code Speicherorte gebunden werden. Beispielsweise kann eine Zeile des Quellcodes für eine C++-Vorlage an jede Code Sequenz gebunden werden, die aus der Vorlage generiert wird. Die Debugsitzung kann ein Haltepunkt gebundenes Ereignis verwenden, um die Code Kontexte aufzuzählen, die beim Senden des Ereignisses an einen Haltepunkt gebunden wurden. Weitere Code Kontexte können später gebunden werden, sodass der de möglicherweise mehrere Haltepunkt gebundene Ereignisse für jede Bindungs Anforderung sendet. Allerdings sollte eine de nur ein breakpointfehlerereignis pro Bindungs Anforderung senden.

## <a name="implementation"></a>Implementierung
 Programm gesteuert Ruft das Debugpaket den Sitzungs-Debug-Manager (SDM) auf und übergibt ihm eine [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Schnittstelle, die eine [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) Struktur umschließt, die den festzulegenden Haltepunkt beschreibt. Obwohl Haltepunkte von vielen Formen sein können, werden Sie letztendlich in einen Code-oder Datenkontext aufgelöst.

 Der SDM übergibt diesen Aufruf an jede relevante de, indem er seine [createperdingbreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) -Methode aufruft. Wenn die de den Breakpoint behandelt, wird eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstelle erstellt und zurückgegeben. Der SDM sammelt diese Schnittstellen und übergibt sie als einzelne Schnittstelle an das Debugpaket `IDebugPendingBreakpoint2` .

 Bisher wurden keine Ereignisse generiert.

 Das Debugpaket versucht dann, den ausstehenden Breakpoint an den Code oder die Daten zu binden, indem [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)aufgerufen wird, der von de implementiert wird.

 Wenn der Breakpoint gebunden ist, sendet der de eine [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) -Ereignis Schnittstelle an das Debugpaket. Das Debugpaket verwendet diese Schnittstelle, um alle Code Kontexte (oder den einzelnen Datenkontext) aufzuzählen, die an den Haltepunkt gebunden sind, indem [enumboundbreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)aufgerufen wird, die eine oder mehrere [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) -Schnittstellen zurückgibt. Die [getbreakpointresolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) -Schnittstelle gibt eine [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) -Schnittstelle zurück, und [getresolutioninfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) gibt eine [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Union zurück, die den Code oder den Datenkontext enthält.

 Wenn die de den Breakpoint nicht binden kann, sendet Sie eine einzelne [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) -Ereignis Schnittstelle an das Debugpaket. Das Debugpaket Ruft den Fehlertyp (Fehler oder Warnung) und die Informations Meldung durch Aufrufen von [geterrorbreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)ab, gefolgt von [getbreakpointresolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) und [getresolutioninfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Dadurch wird eine [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) -Struktur zurückgegeben, die den Fehlertyp und die Meldung enthält.

 Wenn eine de einen Haltepunkt behandelt, ihn aber nicht binden kann, wird ein Fehler vom Typ zurückgegeben `BPET_TYPE_ERROR` . Das Debugpaket antwortet, indem ein Fehler Dialogfeld angezeigt wird, und die IDE fügt ein Ausrufezeichen in das breakpointsymbol links neben der Quell Code Zeile ein.

 Wenn eine de einen Haltepunkt behandelt, kann Sie nicht binden, aber eine andere von de bindet Sie möglicherweise, Sie gibt eine Warnung zurück. Die IDE antwortet, indem ein Frage Symbol innerhalb des breakpointsymbols links neben der Quell Code Zeile platziert wird.

## <a name="see-also"></a>Weitere Informationen
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
