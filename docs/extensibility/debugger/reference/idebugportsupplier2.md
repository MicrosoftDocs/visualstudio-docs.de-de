---
description: Diese Schnittstelle stellt Ports für den Sitzungs-Debug-Manager (SDM) bereit.
title: IDebugPortSupplier2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5e9523212ea83182e69e83b4f8353f1a9ba7dd8c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172038"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Diese Schnittstelle stellt Ports für den Sitzungs-Debug-Manager (SDM) bereit.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um einen Port Lieferanten darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Ein-Befehl `CoCreateInstance` mit einem portlieferant `GUID` gibt diese Schnittstelle zurück (Dies ist die übliche Methode zum Abrufen dieser Schnittstelle). Beispiel:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Ein Rückruf von [getportsupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) gibt diese Schnittstelle zurück, die den aktuellen von verwendeten Port Lieferanten darstellt [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [Getportsupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) gibt diese Schnittstelle zurück, die den Port Lieferanten darstellt, der den Port erstellt hat.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) stellt eine Liste von `IDebugPortSupplier` Schnittstellen dar (die `IEnumDebugPortSuppliers` Schnittstelle wird von [enumportsuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)abgerufen, die alle bei registrierten Port Lieferanten darstellt [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortSupplier2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ruft den Namen des Port Anbieters ab.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ruft den Bezeichner des Port Anbieters ab.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ruft einen Port von einem Port Lieferanten ab.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Listet die Ports auf, die bereits vorhanden sind.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Überprüft, ob ein Port Lieferant das Hinzufügen neuer Ports unterstützt.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Fügt einen Port hinzu.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Entfernt einen Port.|

## <a name="remarks"></a>Bemerkungen
Ein Port Lieferant kann sich selbst anhand des Namens und der ID identifizieren, Ports hinzufügen und entfernen und alle Ports auflisten, die der Port Lieferant bereitstellt.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
