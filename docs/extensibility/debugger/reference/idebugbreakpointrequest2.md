---
description: Die IDebugBreakPointRequest2-Schnittstelle stellt die Informationen dar, die zum Erstellen und Binden von Haltepunkten erforderlich sind.
title: IDebugBreakpointRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e7d13c945de1358265a5eb92769192ce736be49
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162354"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Diese Schnittstelle stellt die Informationen dar, die erforderlich sind, um beliebige Haltepunkt Typen zu erstellen und zu binden.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Sitzungs-Debug-Manager (SDM) implementiert in der Regel diese Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die Debug-Engine (de) empfängt diese Schnittstelle über einen aufzurufenden Befehl zum Erstellen eines ausstehenden [Breakpoints.](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Durch einen Aufrufen von " [getbreakpointrequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) " kann diese Schnittstelle von der "de" abgerufen werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBreakpointRequest2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ruft den Haltepunkt-Stellungstyp dieser Haltepunkt Anforderung ab.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ruft die Haltepunkt-Anforderungs Informationen ab, die diese breakpointanforderung beschreiben.|

## <a name="remarks"></a>Bemerkungen
 Nachdem das Programm, das gedebuggt wurde, geladen wurde, bindet ein [Bindungs](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) Vorgang einen ausstehenden Haltepunkt an den angeforderten Speicherort im Programm.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Zwick](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
