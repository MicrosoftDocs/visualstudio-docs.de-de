---
description: Diese Schnittstelle listet die Ports eines Computers oder eines Port Anbieters auf.
title: IEnumDebugPorts2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4b93aa34870d05b9a4ec0a9a0aa92f681735dfe3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224459"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Diese Schnittstelle listet die Ports eines Computers oder eines Port Anbieters auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um eine Liste der vom Lieferanten erstellten Ports darzustellen. Diese Schnittstelle wird von Visual Studio zur Unterstützung des eigenen Port Anbieters implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [enumports](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) auf, um diese Schnittstelle zu erhalten, die eine Liste der vom Port Lieferanten erstellten Ports darstellt. Rufen Sie [enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) auf, um diese Schnittstelle zu erhalten, die eine Liste der auf dem Datenträger gespeicherten Ports darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugPorts2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Ruft eine angegebene Anzahl von Ports in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Überspringt eine angegebene Anzahl von Ports in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ruft die Anzahl der Ports in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird von Visual Studio verwendet, um eine Liste von Ports aufzufüllen, die zum Anhängen an Prozesse verwendet werden.

 Diese Schnittstelle wird von einer Debug-Engine in der Regel nicht verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
