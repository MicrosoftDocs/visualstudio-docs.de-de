---
description: Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn eine Eigenschaft, die einem bestimmten Dokument zugeordnet ist, zerstört wird.
title: IDebugPropertyDestroyEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34f5a726d8d77a3d12f1d390f70f7bbc30a3abb4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167996"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn eine Eigenschaft, die einem bestimmten Dokument zugeordnet ist, zerstört wird.

## <a name="syntax"></a>Syntax

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft zerstört wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle. Diese Schnittstelle wird implementiert, wenn die de zuvor eine Eigenschaft erstellt hat, die einem Skript zugeordnet ist. Wenn Sie die Eigenschaft zerstören, wird das zugehörige Skript aus der IDE entfernt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de erstellt und sendet dieses Ereignis Objekt, um zu melden, dass eine Eigenschaft zerstört wurde. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle wird die-Methode von gezeigt `IDebugPropertyDestroyEvent2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Ruft die Eigenschaft ab, die zerstört werden soll.|

## <a name="remarks"></a>Bemerkungen
 Ausführliche Informationen dazu, warum diese Ereignisse verwendet werden, finden Sie in den Hinweisen zu [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) .

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
