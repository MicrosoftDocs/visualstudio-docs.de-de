---
description: Diese Schnittstelle stellt ein Quelldokument dar.
title: IDebugDocument2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96bf5821cb463b8a99f7376cb99b81ab8cae2206
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167346"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Diese Schnittstelle stellt ein Quelldokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Implementiert in der Regel diese Schnittstelle. Eine Debug-Engine (de) kann diese Schnittstelle auch implementieren, wenn Sie den Quellcode bereitstellen muss und die Quelle auf dem Datenträger nicht vorhanden ist.  In solchen Fällen würde de de auch [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -und [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) -Schnittstellen sowie einige zusätzliche Methoden für die [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) -und [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) -Schnittstellen implementieren.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden in den `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` Schnittstellen,, und `IDebugActivateDocumentEvent2` geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocument2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einer von mehreren Formularen ab.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft den Klassen Bezeichner des Dokuments ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird nur implementiert, wenn die de den Quellcode bereitstellt. Wenn Sie z. b. das Skript auf einer HTML-Seite Debuggen, stellt das de den Quellcode bereit, da die Quelle heruntergeladen oder dynamisch generiert wird und nicht als Datenträger Datei vorhanden ist. Beim Debuggen von herkömmlichen Sprachen, wie z. b. C++, muss diese Schnittstelle nicht implementiert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
