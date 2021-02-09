---
title: IDebugErrorBreakpointResolution2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1581e9f00e4a2dcb0a7bdab67cfe601b1c9dd05f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888380"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
Diese Schnittstelle stellt die Auflösung eines Breakpoint-Fehlers dar.

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints. Diese Schnittstelle wird verwendet, um zu melden, wo ein Haltepunkt nicht gebunden werden konnte.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufrufen von " [getbreakpointresolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) " gibt diese Schnittstelle zurück, um Informationen darüber bereitzustellen, wo der Breakpoint nicht gebunden werden konnte. Die [geterrorbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) -Methode ruft die [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Schnittstelle ab.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugErrorBreakpointResolution2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den breakpointtyp ab.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur breakpointauflösung ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
