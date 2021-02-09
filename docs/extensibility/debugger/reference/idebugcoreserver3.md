---
title: IDebugCoreServer3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6faa47bc107c8d00864307bdb6802908e085652
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928469"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Diese Schnittstelle ermöglicht den Zugriff auf Informationen über den Server, in dem der Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von einer [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle abzurufen. Bei einem [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) -Rückruf kann diese Schnittstelle ebenfalls zurückgegeben werden. Diese Schnittstelle wird am häufigsten von einem benutzerdefinierten Port Lieferanten verwendet, um Programme auf einem Server (lokal oder Remote) zu starten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in der [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers ab.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Server namens ab.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Weist bestimmte debugengines an, automatisch an Prozesse anzufügen, wenn diese Prozesse starten.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn der automatische Anfüge Vorgang fehlschlägt.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz einer Debug-Engine auf dem Server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag ab, das angibt, ob sich der Server auf demselben Computer wie der Aufrufer befindet.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert ab, der das Protokoll angibt, das für die Kommunikation mit dem Server verwendet wird.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle Einstellungen für das automatische anfügen für alle Debug-engines, die dieser Server kennt.|

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefinierter Port Lieferant empfängt die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle bei einem [Ereignis Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md). Die- `IDebugCoreServer3` Schnittstelle kann von dieser Schnittstelle abgerufen werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
