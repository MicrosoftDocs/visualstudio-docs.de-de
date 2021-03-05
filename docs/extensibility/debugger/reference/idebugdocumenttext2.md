---
description: Diese Schnittstelle stellt ein Textdokument dar.
title: IDebugDocumentText2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1c5928362616466985a6f88102ffcbf4377444
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154209"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Diese Schnittstelle stellt ein Textdokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine (de) implementiert diese Schnittstelle, wenn der Quellcode, den Sie bereitstellen muss, in Textform ist. Da dies der typische Fall ist, sollte die-Schnittstelle von der de implementiert werden, wenn die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle von de implementiert wird `IDebugDocumentText2` .

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie die- `QueryInterface` Methode, um diese Schnittstelle von einer `IDebugDocument2` Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden der- `IDebugDocument2` Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Ruft die Größe des Texts an dieser Position im Dokument ab.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Ruft den Text an der angegebenen Position im Dokument ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Objekt, das diese Schnittstelle implementiert, muss auch die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle implementieren, die die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle für ein [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) -Objekt bereitstellt.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
