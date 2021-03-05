---
description: Diese Schnittstelle stellt einen Fehler-oder Warnungs Haltepunkt dar, z. b. einen ungültigen Speicherort, einen ungültigen Ausdruck oder die Gründe, warum der ausstehende Haltepunkt nicht gebunden wurde (der Code wurde noch nicht geladen usw.).
title: IDebugErrorBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91697ebad462f3d1e953aa42d74bf5a96757886a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153156"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Diese Schnittstelle stellt einen Fehler-oder Warnungs Haltepunkt dar, z. b. einen ungültigen Speicherort, einen ungültigen Ausdruck oder die Gründe, warum der ausstehende Haltepunkt nicht gebunden wurde (der Code wurde noch nicht geladen usw.).

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints. Diese Schnittstelle wird verwendet, um Probleme mit der Bindung eines Breakpoints zu melden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird durch einen Aufrufen von [geterrorbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) abgerufen. Diese Schnittstelle kann auch (als Teil einer durch eine [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) -Schnittstelle dargestellten Liste) durch einen [kanbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) -oder [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)-Befehl zurückgegeben werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugErrorBreakpoint2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Breakpoint ab, der den Fehler verursacht hat.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die breakpointfehlerauflösung ab, die den Fehler beschreibt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
