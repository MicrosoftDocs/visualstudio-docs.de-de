---
title: IDebugMemoryContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727425"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Diese Schnittstelle stellt eine Position im Adressraum des Computers dar, auf dem das gedestete Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Adresse im Arbeitsspeicher darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird von einem [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) -oder [getmemorycontext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) -Befehl zurückgegeben. Außerdem geben Aufrufe zum [addieren](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) und [subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) neue Kopien dieser Schnittstelle zurück, nachdem die entsprechende arithmetische Operation angewendet wurde.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugMemoryContext2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ruft den vom Benutzer anzeigbaren Namen für diesen Kontext ab.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ruft Informationen ab, die diesen Kontext beschreiben.|
|[Add (Hinzufügen)](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Fügt der Adresse des aktuellen Kontexts einen angegebenen Wert hinzu, um einen neuen Kontext zu erstellen.|
|[Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrahiert einen angegebenen Wert von der Adresse des aktuellen Kontexts, um einen neuen Kontext zu erstellen.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Vergleicht zwei Kontexte in der durch Compare-Flags gekennzeichneten Weise.|

## <a name="remarks"></a>Bemerkungen
 Das Fenster Arbeits **Speicher** von Visual Studio ruft [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) auf, um die `IDebugMemoryContext2` Schnittstelle abzurufen, die den ausgewerteten Ausdruck für die Speicheradresse enthält. Dieser Kontext wird dann an " [leseat](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) " und "Write" weitergegeben, um die zu lesende oder zu Schreib [Ende](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) Adresse anzugeben.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
