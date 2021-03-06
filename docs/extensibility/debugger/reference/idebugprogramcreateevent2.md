---
description: Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn ein Programm an angefügt wird.
title: IDebugProgramCreateEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 535d54e0c7cdd4b175cd76c9d1fbe9ce240b5ccf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151622"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn ein Programm an angefügt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der von de oder der benutzerdefinierte Port Lieferant implementiert diese Schnittstelle, um zu melden, dass ein Programm erstellt wurde, in der Regel zu dem Zeitpunkt, an dem das Programm angefügt wird. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet die- `QueryInterface` Methode für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der von de oder der benutzerdefinierte Port Lieferant erstellt und sendet dieses Ereignis Objekt, um die Erstellung eines Programms zu melden. Der de sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion, die von SDM bereitgestellt wird, wenn es an das Programm angefügt wird, das gerade deentschlgt wird. Der benutzerdefinierte Port Lieferant sendet dieses Ereignis mithilfe der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle.

## <a name="remarks"></a>Bemerkungen
 Der benutzerdefinierte Port Lieferant veröffentlicht eine neue [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle, indem er [publishprogramnode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)aufruft.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
