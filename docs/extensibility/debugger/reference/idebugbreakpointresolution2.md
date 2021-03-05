---
description: Diese Schnittstelle stellt die Informationen dar, die einen gebundenen Haltepunkt beschreiben.
title: IDebugBreakpointResolution2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31543b574006609cb22e6cf505771840678a97fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143323"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Diese Schnittstelle stellt die Informationen dar, die einen gebundenen Haltepunkt beschreiben.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints. Diese Schnittstelle stellt eine Beschreibung eines gebundenen halte Punkts bereit, den der sitzungsdebug-Manager verwendet, wenn ein Benutzer die Eigenschaften eines halte Punkts anzeigt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufrufen von " [getbreakpointresolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) " gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBreakpointResolution2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Breakpoints ab, der durch diese Auflösung dargestellt wird.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur breakpointauflösung ab, die diesen Haltepunkt beschreiben.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
