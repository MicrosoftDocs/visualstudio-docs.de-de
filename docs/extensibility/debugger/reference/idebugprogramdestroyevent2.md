---
title: IDebugProgramDestroyEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722592"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn ein Programm bis zum Abschluss ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der von de oder der benutzerdefinierte Port Lieferant implementiert diese Schnittstelle, um zu melden, dass ein Programm beendet wurde und nicht mehr zum Debuggen verfügbar ist. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der von de oder der benutzerdefinierte Port Lieferant erstellt und sendet dieses Ereignis Objekt, um die Beendigung eines Programms zu melden. Der de sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion, die von SDM bereitgestellt wird, wenn es an das Programm angefügt wird, das gerade deentschlgt wird. Der benutzerdefinierte Port Lieferant sendet dieses Ereignis mithilfe der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle wird die-Methode von gezeigt `IDebugProgramDestroyEvent2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Ruft den Exitcode des Programms ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
