---
description: Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird.
title: IDebugProgram2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b4854150d6581d80804b4c29246bf6db016b5acb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159912"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) und ein benutzerdefinierter Port Lieferant implementieren diese Schnittstelle, um ein Programm in einem Prozess darzustellen. Der Sitzungs-Debug-Manager (SDM) implementiert auch diese Schnittstelle, um die [anzufügenden](../../../extensibility/debugger/reference/idebugprogram2-attach.md)Informationen bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden in mehreren Schnittstellen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgram2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Listet die Threads auf, die in diesem Programm ausgeführt werden.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ruft den Namen des Programms ab.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ruft den Prozess ab, in dem das Programm ausgeführt wird.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Beendet das Programm.|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Wird an dieses Programm angefügt.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bestimmt, ob eine Debug-Engine (de) vom Programm getrennt werden kann.|
|[Trennen](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Trennt den Debugger von diesem Programm.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ruft eine Globally Unique Identifier für dieses Programm ab.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ruft Programm Eigenschaften ab.|
|[Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung dieses Programms mit dem Status "beendet" fort. Ein vorheriger Ausführungs Status ist gelöscht.|
|[Fortsetzen](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung dieses Programms mit dem Status "beendet" fort. Ein vorheriger Ausführungs Status wird beibehalten.|
|[Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt aus.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Fordert an, dass dieses Programm die Ausführung beendet, wenn ein Thread das nächste Mal Code ausführt.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ruft den Namen und den Bezeichner der Debug-Engine (de) ab, die dieses Programm ausgeführt wird.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Listet die Code Kontexte für eine angegebene Position in einer Quelldatei auf.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ruft die Arbeitsspeicher Bytes für dieses Programm ab.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ruft den disassemblystream für dieses Programm oder einen Teil dieses Programms ab.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Listet die Module auf, die dieses Programm geladen hat und ausgeführt wird.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ruft das Update für die Bearbeitung und Fortsetzung (ENC) für dieses Programm ab.<br /><br /> Eine benutzerdefinierte Debug-Engine implementiert diese Methode nicht (Sie sollte immer zurückgeben `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Listet die Codepfade dieses Programms auf.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Schreibt ein dump in eine Datei.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Bemerkungen
 Ein Programm ist ein Thread Container, der in einer bestimmten Lauf Zeit Architektur ausgeführt wird, während ein Prozess aus mindestens einem Programm besteht.

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
