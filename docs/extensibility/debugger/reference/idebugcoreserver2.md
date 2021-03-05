---
description: Diese Schnittstelle dient zur Darstellung und zum Abrufen von Informationen von einem Server auf einem Computer im Netzwerk.
title: IDebugCoreServer2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 871f7ea5671fa4f3c615d84e0591bd331f945ccc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163134"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Diese Schnittstelle dient zur Darstellung und zum Abrufen von Informationen von einem Server auf einem Computer im Netzwerk.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio implementiert, um einen Server darzustellen. Jede Instanz von Visual Studio erstellt eine Instanz dieser Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein benutzerdefinierter Port Lieferant empfängt diese Schnittstelle in einem [Ereignis Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Eine Debug-Engine kann diese Schnittstelle indirekt durch einen get-Befehl von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) abrufen (der [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)zurückgibt, eine Schnittstelle, die von abgeleitet ist `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugCoreServer2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und die Attribute eines Computers ab.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers ab.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft einen Port Lieferanten ab, der auf einem Computer vorhanden ist.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft einen Port ab, der bereits auf einem Computer vorhanden ist.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Port Lieferanten auf einem Computer.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Computer Dienstprogramme für einen Computer ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird auch von Visual Studio verwendet, um Prozesse zu durchsuchen, die auf Computern im Netzwerk ausgeführt werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
