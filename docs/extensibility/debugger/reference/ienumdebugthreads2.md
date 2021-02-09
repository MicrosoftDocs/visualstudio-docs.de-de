---
title: IEnumDebugThreads2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e3771545d4a5fe545382344d17ed5ea929999d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852777"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Diese Schnittstelle listet die Threads auf, die in der aktuellen Debugsitzung ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Threads in einem Programm darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [enumthreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) auf, um diese Schnittstelle abzurufen, die eine Liste aller Threads in allen Programmen darstellt, die in einem Prozess ausgeführt werden. Rufen Sie [enumreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) auf, um diese Schnittstelle abzurufen, die eine Liste der in einem Programm ausgelaufenden Threads darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugThreads2` .

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Ruft eine angegebene Anzahl von Threads in der enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Überspringt eine angegebene Anzahl von Threads in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ruft die Anzahl der Threads in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle normalerweise ab, um das **Thread** Fenster zu aktualisieren und den ersten Thread der Liste zu erhalten, um [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)und [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)aufzurufen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
