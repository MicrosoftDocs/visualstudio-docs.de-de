---
description: Diese Schnittstelle stellt einen Prozess dar, der auf einem Port ausgeführt wird.
title: IDebugProcess2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 131eacba321bac70c75b77faf33b18aae0135e55
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150262"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Diese Schnittstelle stellt einen Prozess dar, der auf einem Port ausgeführt wird. Wenn der Port der lokale Port ist, `IDebugProcess2` stellt normalerweise einen physischen Prozess auf dem lokalen Computer dar.

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten Port Lieferanten implementiert, um Programme als Gruppe zu verwalten. Diese Schnittstelle muss vom Port Lieferanten implementiert werden.

 Außerdem implementiert eine Debug-Engine diese Schnittstelle, wenn Sie das Starten eines Programms durch [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird hauptsächlich vom Sitzungs-Debug-Manager (SDM) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert werden.

 Aufrufen von [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oder [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) , um diese Schnittstelle zu erhalten. Diese Schnittstelle wird auch durch Aufrufen von zurückgegeben `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcess2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ruft eine Beschreibung des Prozesses ab.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Listet die Programme auf, die in diesem Prozess enthalten sind.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ruft den Titel, den anzeigen Amen oder den Dateinamen des Prozesses ab.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ruft die Instanz eines Computer Servers ab, auf dem dieser Vorgang ausgeführt wird.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Beendet den Prozess.|
|[Anfügen](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Wird an den Prozess angefügt.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Bestimmt, ob der Prozess vom SDM getrennt werden kann.|
|[Trennen](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Trennt den Debugger vom Prozess.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ruft den System Prozess Bezeichner ab.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ruft eine Globally Unique Identifier für diesen Prozess ab.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> Veraltet|Ruft den Namen der Sitzung ab, die den Prozess debuggt.<br /><br /> Veraltet. sollte immer zurückgeben `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Listet die Threads auf, die im Prozess ausgeführt werden.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Fordert an, dass das nächste Programm, in dem der Code ausgeführt wird, beendet wird.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ruft den Port ab, auf dem dieser Prozess ausgeführt wird.|

## <a name="remarks"></a>Bemerkungen
 Eine `IDebugProcess2` enthält mindestens eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
