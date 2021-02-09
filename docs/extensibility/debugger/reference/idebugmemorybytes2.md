---
title: IDebugMemoryBytes2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9d4ee145d900a79a48db44f95a125e87bd10f67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851243"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Diese Schnittstelle stellt Bytes des Arbeitsspeichers dar.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um Bytes im Arbeitsspeicher darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
- [Getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) gibt diese Schnittstelle zurück, um den Zugriff auf den Systemspeicher bereitzustellen. Von [getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) und [getmemorybytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) wird diese Schnittstelle zurückgegeben, um den Zugriff auf die Bytes eines Objekts zu ermöglichen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugMemoryBytes2` .

|Methode|Beschreibung|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Liest eine Byte Sequenz, beginnend an einem angegebenen Speicherort.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Schreibt `dwCount` bytes, beginnend bei `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ruft die Größe des Arbeitsspeichers in Bytes ab, der durch diese Schnittstelle dargestellt wird.|

## <a name="remarks"></a>Bemerkungen
 Für-Eigenschaften bietet eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle, die ein Array darstellt, eine `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf die Werte in diesem Array.

 Die Arbeits **Speicher Ansicht** von Visual Studio ruft [getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) auf, um eine `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf den Systemspeicher abzurufen. Die Adresse, auf die zugegriffen werden soll, wird durch Analysieren des als Adresse eingegebenen Ausdrucks in die Speicher Ansicht und anschließendes Auswerten des analysierten Ausdrucks mithilfe von [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer `IDebugProperty2` Schnittstelle abgerufen. Ein [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) -Rückruf gibt das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) zurück, das die Speicheradresse beschreibt. Dieser Speicher Kontext wird dann an "read [at](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) " und " [Write](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)" weitergegeben.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
