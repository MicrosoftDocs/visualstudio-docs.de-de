---
description: Diese Schnittstelle stellt einen debugsport auf einem Computer dar.
title: IDebugPort2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f78db8ba9a29b40d111dc5a82827395b100302b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169482"
---
# <a name="idebugport2"></a>IDebugPort2
Diese Schnittstelle stellt einen debugsport auf einem Computer dar.

## <a name="syntax"></a>Syntax

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um einen Debugport auf einem Computer darzustellen.

 Wenn der Port Sende Port Ereignisse unterstützt, muss er auch die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle implementieren, um eine Schnittstelle zu unterstützen, die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> wiederum die [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle bietet.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Aufrufe von [getPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) geben diese Schnittstelle zurück, die den angeforderten Port darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPort2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Portnamen zurück.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Port Bezeichner zurück.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zurück, die zum Erstellen eines Ports verwendet wird (falls verfügbar).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Port Lieferanten für diesen Port zurück.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle zum Prozess zurück, wenn der Bezeichner des Prozesses angegeben ist.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Listet alle Prozesse auf, die auf einem Port ausgeführt werden.|

## <a name="remarks"></a>Bemerkungen
 Der lokale Port ermöglicht den Zugriff auf alle Prozesse und Programme, die auf dem lokalen Computer ausgeführt werden. Andere Ports stellen möglicherweise eine serielle Kabelverbindung mit einem Windows CE basierten Gerät oder eine Netzwerkverbindung mit einem nicht-DCOM-Computer dar. Die `IDebugPort2` -Schnittstelle wird verwendet, um den Namen und den Bezeichner eines Ports zu suchen und alle Prozesse aufzulisten, die auf dem Port ausgeführt werden. Funktionen zum Starten und Beenden von Prozessen auf dem Port werden in der- `IDebugPortEx2` Schnittstelle implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
