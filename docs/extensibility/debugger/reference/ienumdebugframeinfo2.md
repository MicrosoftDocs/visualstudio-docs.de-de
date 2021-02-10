---
title: IEnumDebugFrameInfo2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fdc2006b45a664496615988251081f1000cdb428
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956286"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Diese Schnittstelle listet [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Strukturen bereitzustellen, die die aktuelle-aufrufsliste beschreibt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio ruft [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um diese Schnittstelle zu erhalten, wenn ein Breakpoint, eine Ausnahme oder ein Halt in einem Programm auftritt, das gerade deentschlgt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugFrameInfo2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Ruft eine angegebene Anzahl von [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Überspringt eine angegebene Anzahl von [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ruft die Anzahl der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle als ersten Schritt ab, um einen Haltepunkt, eine Ausnahme oder eine vom benutzergenerierte Pause für das Programm zu behandeln, das gerade deentschlgt wird. Die Liste der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen stellt die aktuelle Aufrufliste mit dem aktuellen Funktions aufrufam Anfang der Liste und dem ältesten Funktions aufrufam Ende der Liste dar. Jede `FRAMEINFO` stellt einen Stapel Rahmen dar, einen Kontext, in dem Ausdrücke ausgewertet und lokale Variablen angesehen werden können.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
