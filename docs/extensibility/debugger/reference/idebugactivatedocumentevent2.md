---
title: IDebugActivateDocumentEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ec3168a7e104e20bbb53607b4bd7a6acd8e79e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904658"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Die Debug-Engine (de) verwendet diese Schnittstelle, um ein Dokument anzufordern, das geladen werden soll.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, wenn eine Quelldatei geöffnet werden muss. Diese Schnittstelle wird nur von Debug-engines implementiert, die mit oder einem Teil von Skript Interpretern funktionieren. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, wenn eine Quelldatei geöffnet werden muss. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugActivateDocumentEvent2` .

|Methoden|BESCHREIBUNG|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ruft das zu Aktivier-Dokument ab.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ruft den Dokument Kontext ab, der die Position im Dokument beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Ein typisches Szenario, in dem diese Schnittstelle verwendet wird, wenn im Skriptcode auf einer HTML-Seite ein Analysefehler auftritt, sendet das Skript de diese Schnittstelle an SDM, damit das Dokument mit dem Analysefehler angezeigt werden kann.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
