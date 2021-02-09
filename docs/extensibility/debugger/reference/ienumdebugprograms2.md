---
title: IEnumDebugPrograms2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 04566b4a8dae7f25f799d08780c93936009adef8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890746"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Diese Schnittstelle listet die Programme auf, die in der aktuellen Debugsitzung ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste der Programme bereitzustellen, die von der de debuggt werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio ruft [enumprogramme](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf, um diese Schnittstelle zu erhalten. [Enumprogramme](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) werden von Visual Studio nicht verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugPrograms2` .

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Ruft eine angegebene Anzahl von Programmen in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Überspringt eine angegebene Anzahl von Programmen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ruft die Anzahl der Programme in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle für Folgendes:

- Füllen Sie das Fenster **Module** (durch Aufrufen von [enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) und anschließendes Aufrufen von [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) für jedes Programm).

- Füllen Sie die Liste **an den Prozess anhängen** (durch Aufrufen von und anschließendes `IDebugProcess2::EnumPrograms` Aufrufen von [QueryInterface](/cpp/atl/queryinterface) für jede [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle zum Abrufen einer [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) -Schnittstelle).

- Generiert eine Liste von des, die jedes Programm im Prozess Debuggen können (mithilfe von [getengineingefo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Anwenden von "Bearbeiten und Fortfahren"-Aktualisierungen (ENC) auf jedes Programm (durch Aufrufen von "IDebugProcess2:: enumprograms" und anschließendes Aufrufen von [getencupdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
