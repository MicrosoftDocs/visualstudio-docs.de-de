---
title: IDebugEngine2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c38dc023c44e0c1743fd9d35dbe65befda405f4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919923"
---
# <a name="idebugengine2"></a>IDebugEngine2
Diese Schnittstelle stellt eine Debug-Engine (de) dar. Es wird zum Verwalten verschiedener Aspekte einer Debugsitzung verwendet, von der Erstellung von Breakpoints bis zum Festlegen und Löschen von Ausnahmen.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten Programm zur Verwaltung des Debuggens von Programmen implementiert. Diese Schnittstelle muss von der de implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird vom Sitzungs-Debug-Manager (SDM) zum Verwalten der Debugsitzung aufgerufen, einschließlich der Verwaltung von Ausnahmen, der Erstellung von Breakpoints und der Reaktion auf synchrone Ereignisse, die von der de gesendet werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEngine2` .

|Methode|Beschreibung|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Erstellt einen Enumerator für alle Programme, die von einer de debuggt werden.|
|[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Fügt eine de an ein Programm an.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Erstellt einen ausstehenden Haltepunkt in der de.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Gibt an, wie eine bestimmte Ausnahme von der de behandelt werden soll.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Entfernt die angegebene Ausnahme, sodass Sie nicht mehr von der Debug-Engine verarbeitet wird.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Entfernt die Liste der Ausnahmen, die die IDE für eine bestimmte Lauf Zeit Architektur oder-Sprache festgelegt hat.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ruft die GUID der de ab.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informiert eine de, dass das angegebene Programm atypisch beendet wurde und dass die de alle Verweise auf das Programm bereinigen und ein Programm zerstörungsereignis senden soll.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wird von SDM aufgerufen, um anzugeben, dass ein synchrones Debugereignis empfangen und verarbeitet wurde, das zuvor von der de an die SDM gesendet wurde.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Legt das Gebiets Schema der de fest.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Legt den Registrierungs Stamm fest, der zurzeit von der de verwendet wird.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Legt eine Metrik fest.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Fordert an, dass alle Programme, die von diesem debuggt werden, die Ausführung abbrechen, wenn einer ihrer Threads das nächste Mal ausgeführt wird.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
