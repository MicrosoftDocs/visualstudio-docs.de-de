---
title: IDebugBreakpointRequest3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6e42111ca0c8b357a7f8841511cf935694a30b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893060"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Diese Schnittstelle stellt die Informationen dar, die erforderlich sind, um beliebige Haltepunkt Typen zu erstellen und zu binden. Es handelt sich um eine Erweiterung von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Sitzungs-Debug-Manager (SDM) implementiert in der Regel diese Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die Debug-Engine (de) greift durch Aufrufen von [QueryInterface](/cpp/atl/queryinterface) in der IDebugBreakpointRequest2-Schnittstelle auf diese Schnittstelle zu, die in einem Aufruf von [creatependingbreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)empfangen wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)geerbten Methoden macht die- `IDebugBreakpointRequest3` Schnittstelle die folgende Methode verfügbar.

|Methode|Beschreibung|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ruft die Haltepunkt-Anforderungs Informationen ab, die diese breakpointanforderung beschreiben.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird verwendet, um der de über die [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur zusätzliche Informationen bereitzustellen. Diese zusätzlichen Informationen umfassen die Hersteller-ID (in Form einer GUID), den Namen eines Ablauf Verfolgungs Punkts und den Namen einer breakpointeinschränkung.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
