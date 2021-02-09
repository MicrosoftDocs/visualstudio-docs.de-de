---
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
ms.openlocfilehash: 44e0bc66d9f385a41f0f43af7217738e40e69126
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887119"
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

|Methode|Beschreibung|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des zu erstellenden Ports ab.|

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten und wird für diese Schnittstelle nicht verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
