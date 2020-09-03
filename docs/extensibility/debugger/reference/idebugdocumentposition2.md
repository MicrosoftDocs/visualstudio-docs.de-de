---
title: IDebugDocumentPosition2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731641"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Diese Schnittstelle stellt eine abstrakte Position in einer Quelldatei dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio normalerweise implementiert. Eine Debug-Engine (de) würde diese Schnittstelle auch implementieren, wenn Sie Ihren eigenen Quellcode bereitstellen muss (wie wenn die de die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle implementiert).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird als Argument an [enumcodekontexte](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)übermittelt. Sie wird auch als Teil einer [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (insbesondere einer [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur) bereitgestellt, die wiederum Teil der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur ist, die zum Erstellen eines ausstehenden halte Punkts verwendet wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocumentPosition2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ruft den Dateinamen der Quelldatei ab, die diese Dokument Position enthält.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ruft das enthaltende Dokument ab.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bestimmt, ob diese Position im angegebenen Dokument enthalten ist.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ruft den Bereich für diese Dokument Position ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
