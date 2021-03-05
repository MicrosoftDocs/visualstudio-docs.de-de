---
description: Diese Schnittstelle beschreibt einen Port.
title: IDebugPortRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ca2d1d59c66c87c2dbb0fc256481d35ad590dbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142621"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Diese Schnittstelle beschreibt einen Port. Diese Beschreibung wird verwendet, um den Port einem Port Lieferanten hinzuzufügen.

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio normalerweise implementiert, um einen Debugport von einem Port Lieferanten zu erhalten.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird an [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) übermittelt, um einen Debugport zu erstellen. Ein [getportrequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) -Rückruf gibt diese Schnittstelle zurück, die die Anforderung darstellt, die zuerst zum Erstellen des Ports verwendet wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortRequest2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des zu erstellenden Ports ab.|

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten und wird für diese Schnittstelle nicht verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
