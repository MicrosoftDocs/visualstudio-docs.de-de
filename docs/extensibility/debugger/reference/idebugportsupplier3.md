---
title: IDebugPortSupplier3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d45d8d93f26ef01fb184811a87b4f4fcc4483340
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840235"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Mit dieser Schnittstelle kann ein Aufrufer ermitteln, ob ein Port Lieferant Ports (durch das Schreiben auf einen Datenträger) zwischen den Aufrufen des Debuggers beibehalten und dann eine Liste mit diesen beibehaltenen Ports erhalten soll.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um die Beibehaltung oder Speicherung von Port Informationen auf dem Datenträger zu unterstützen Diese Schnittstelle muss auf demselben Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für die-Schnittstelle auf `IDebugPortSupplier2` , um diese Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den von der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle geerbten Methoden unterstützt diese Schnittstelle Folgendes:

|Methode|Beschreibung|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob der Port Lieferant Ports (durch das Schreiben auf einen Datenträger) zwischen den Aufrufen des Debuggers beibehalten kann.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt zurück, das verwendet werden kann, um alle Ports aufzuzählen, die von diesem Port Lieferanten auf den Datenträger geschrieben wurden.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Port Lieferant Ports über Aufrufe hinweg beibehalten kann, sollte er diese Schnittstelle implementieren. Ports sollten geladen werden, wenn der Port Lieferant instanziiert wird, und auf den Datenträger geschrieben, wenn der Port Lieferant zerstört wird.

 Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten und wird für diese Schnittstelle nicht verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
