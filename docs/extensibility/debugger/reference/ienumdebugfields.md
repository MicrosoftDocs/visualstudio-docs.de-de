---
description: Diese Schnittstelle stellt eine Auflistung von Objekten dar, die die idebugfield-Schnittstelle implementieren.
title: Ienumdebug-Felder | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad912c7225cb1a8c3d6ca294a4031c19bcd47e9a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226552"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Diese Schnittstelle stellt eine Auflistung von Objekten dar, die die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementieren.

## <a name="syntax"></a>Syntax

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird vom Symbol Anbieter implementiert, um Sätze von Objekten bereitzustellen, die die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementieren. Beachten Sie, dass es sich hierbei nicht um eine com-Standard Enumeration handelt, da die [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) -Methode vorhanden ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird von [getmethodfieldsbyname](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) und [getnamespacesusedataddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)zurückgegeben.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Ruft den nächsten Satz von [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekten aus der-Enumeration ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Setzt die Enumeration auf den ersten Eintrag zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Ruft die Anzahl der Einträge in der-Enumeration ab.|

## <a name="remarks"></a>Bemerkungen

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
