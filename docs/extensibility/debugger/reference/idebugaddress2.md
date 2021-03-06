---
description: Diese Schnittstelle ermöglicht den Zugriff auf die ID des Prozesses, der das Objekt besitzt, dessen Adresse durch diese Schnittstelle repräsentiert wird.
title: IDebugAddress2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3f01472f60996b7094334de8cb2dbd79acac0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143960"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Diese Schnittstelle ermöglicht den Zugriff auf die ID des Prozesses, der das Objekt besitzt, dessen Adresse durch diese Schnittstelle repräsentiert wird.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle implementiert. Diese Schnittstelle ermöglicht den Zugriff auf die ID des Prozesses, der das Objekt besitzt, das mit dieser Adresse verknüpft ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von der [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle geerbt werden, implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Ruft die ID des Prozesses ab, der das Objekt besitzt, das von dieser Schnittstelle dargestellt wird.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
