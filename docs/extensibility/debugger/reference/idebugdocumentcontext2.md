---
title: IDebugDocumentContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 64db2446496d2083d34eefc92afabc3ca541442e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946968"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Diese Schnittstelle stellt eine Position in einem Quelldatei Dokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung für das Debuggen auf Quell Code Ebene. Zusätzlich zu einer Position im Quellcode bietet diese Schnittstelle Methoden zum Vergleichen von Kontexten und Navigieren durch ein Quell Code Dokument.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden für mehrere Schnittstellen, in der Regel die [getdocumentcontext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) -und [getdocumentcontext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) -Schnittstellen, geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocumentContext2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ruft das Dokument ab, das diesen Dokument Kontext enthält.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ruft den anzeigbaren Namen des Dokuments ab, das diesen Dokument Kontext enthält.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Ruft eine Liste aller diesem Dokument Kontext zugeordneten Code Kontexte ab.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ruft die Sprache ab, die diesem Dokument Kontext zugeordnet ist.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Bereich der Datei Anweisung dieses Dokument Kontexts ab.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ruft den Datei Quellbereich dieses Dokument Kontexts ab.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Vergleicht diesen Dokument Kontext mit einem angegebenen Array von Dokument Kontexten.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Verschiebt den Dokument Kontext um eine angegebene Anzahl von Anweisungen oder Zeilen.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
