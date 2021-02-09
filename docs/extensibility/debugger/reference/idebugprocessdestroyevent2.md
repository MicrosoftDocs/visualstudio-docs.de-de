---
title: IDebugProcessDestroyEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c194ef3585a8ba3f0a0ab90e5ea39f4ad3a04622
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861100"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Diese Schnittstelle wird gesendet, wenn ein Prozess beendet wird, das atypisch beendet oder von getrennt wird.

## <a name="syntax"></a>Syntax

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) oder der benutzerdefinierte Port Lieferant implementiert diese Schnittstelle, um zu melden, dass ein Prozess beendet wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der von de oder der benutzerdefinierte Port Lieferant erstellt und sendet dieses Ereignis Objekt, um die Beendigung eines Prozesses zu melden. Der de sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird. Der benutzerdefinierte Port Lieferant sendet dieses Ereignis mithilfe der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
