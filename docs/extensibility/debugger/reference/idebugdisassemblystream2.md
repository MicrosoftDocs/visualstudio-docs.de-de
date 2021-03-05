---
description: Diese Schnittstelle stellt einen Stream von Anweisungen dar.
title: IDebugDisassemblyStream2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 760d77ced3cc07da2dd02c21cf3ed0200df14231
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166566"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Diese Schnittstelle stellt einen Stream von Anweisungen dar.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine implementiert diese Schnittstelle, um die Disassembly eines Programmcodes zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Bei einem Aufrufen der [getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) -Methode wird diese Schnittstelle zurückgegeben.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDisassemblyStream2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest Anweisungen ab der aktuellen Position im disassemblystream.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt den Lese Zeiger im disassemblystream um eine bestimmte Anzahl von Anweisungen relativ zu einer angegebenen Position.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt einen Bezeichner für den Code Speicherort für einen bestimmten Code Kontext zurück.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein Code Kontext Objekt zurück, das einem angegebenen Bezeichner für den Code Speicherort entspricht.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Bezeichner für den Code Speicherort zurück, der den aktuellen codeort darstellt.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument ab, das diesem disassemblystream zugeordnet ist.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Gültigkeitsbereich dieses disassemblystreams ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses disassemblystreams ab.|

## <a name="remarks"></a>Bemerkungen
 Der disassemblystream kann erstellt werden, um den gesamten Adressraum oder nur eine Funktion oder ein Modul innerhalb des Raums darzustellen. Jede Anweisung wird durch eine [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur dargestellt, die durch einen Aufrufder [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) -Methode zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
