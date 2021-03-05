---
description: Mit dieser Schnittstelle kann der Sitzungs-Debug-Manager (SDM) die Programme und Prozesse steuern, die auf einem Port ausgeführt werden.
title: IDebugPortEx2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54da202e6bbaf08216b921afbde2e39f1da3a788
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142790"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Mit dieser Schnittstelle kann der Sitzungs-Debug-Manager (SDM) die Programme und Prozesse steuern, die auf einem Port ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle für das gleiche Objekt, das [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der SDM ruft [QueryInterface](/cpp/atl/queryinterface) auf der-Schnittstelle auf `IDebugPort2` , um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortEx2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Hiermit wird eine ausführbare Datei gestartet.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Nimmt die Ausführung eines Prozesses wieder auf.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Beendet einen Prozess.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ruft die Prozess-ID des Ports selbst ab.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ruft ein Programm ab, das einem Programmknoten zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist normalerweise zwischen dem SDM und dem benutzerdefinierten Port Lieferanten privat.

 Wenn gewünscht, kann eine Debug-Engine (de) in der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die an [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) alten wird, nach dieser Schnittstelle suchen und das Programm mit [launchangeh](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) alten starten. Dies ist jedoch nicht zwingend erforderlich, und eine de kann alle Aktionen ausführen, die erforderlich sind, um das Anforderungs Programm zu starten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
