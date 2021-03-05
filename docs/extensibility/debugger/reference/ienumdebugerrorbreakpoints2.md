---
description: Diese Schnittstelle listet die Fehler Haltepunkte auf, die einem ausstehenden Haltepunkt zugeordnet sind.
title: IEnumDebugErrorBreakpoints2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d770f9613dad30d46f1788aeecb67997388eea75
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224914"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Diese Schnittstelle listet die Fehler Haltepunkte auf, die einem ausstehenden Haltepunkt zugeordnet sind.

## <a name="syntax"></a>Syntax

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio ruft [canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) auf, um diese Schnittstelle abzurufen, die eine Liste von Haltepunkten darstellt, die nicht gebunden werden können, oder [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) zum Abrufen dieser Schnittstelle, die eine Liste von Haltepunkten darstellt, die nicht gebunden wurden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugErrorBreakpoints2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Ruft eine angegebene Anzahl von Fehler Breakpoints in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl von Fehler Breakpoints in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ruft die Anzahl der Fehler Breakpoints in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle enthält eine Liste von [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Schnittstellen, von denen jeder einen Haltepunkt beschreibt, der nicht gebunden werden konnte, und warum er nicht gebunden werden konnte. Visual Studio verwendet die- `IEnumDebugErrorBreakpoint2` Schnittstelle, um die Breakpoints zu aktualisieren, die in der IDE angezeigt werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
