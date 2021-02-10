---
title: IDebugEventCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe81a7d8a07a80f38e771e2cfbac3ec23da54b62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933361"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Diese Schnittstelle wird von der Debug-Engine (de) verwendet, um Debugereignisse an den Sitzungs-Debug-Manager (SDM) zu senden.

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert diese Schnittstelle zum Empfangen von Ereignissen von einer Debug-Engine.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Eine Debug-Engine empfängt diese Schnittstelle in der Regel, wenn die SDM [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten aufruft. Ein Debug-Modul sendet Ereignisse an die SDM, indem das [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)aufgerufen wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEventCallback2` .

|Methode|Beschreibung|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet Benachrichtigungen über Debuggingereignisse an SDM.|

## <a name="remarks"></a>Bemerkungen
 Obwohl [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) angeben, dass eine `IDebugEventCallback2` Schnittstelle verwendet wird, ist dies nicht der Fall, und der Schnittstellen Zeiger ist immer ein NULL-Wert. Stattdessen muss die Debug-Engine die-Schnittstelle verwenden, die im-Befehl `IDebugEventCallback2` zum [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [launchangeh](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten empfangen wird.

 Wenn ein Paket [idebugeventcallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code implementiert, wird dringend empfohlen, dass Sie <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> für die verschiedenen Schnittstellen aufgerufen werden, die an das- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)weitergegeben werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
