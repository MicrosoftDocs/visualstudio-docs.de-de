---
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
ms.openlocfilehash: af72993a4a02ce7d25858bf3bd4f0690e0d30f5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923107"
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

|Methode|Beschreibung|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Ruft die Größe des Texts an dieser Position im Dokument ab.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Ruft den Text an der angegebenen Position im Dokument ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Objekt, das diese Schnittstelle implementiert, muss auch die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle implementieren, die die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle für ein [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) -Objekt bereitstellt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
