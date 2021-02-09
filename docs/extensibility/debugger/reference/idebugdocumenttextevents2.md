---
title: IDebugDocumentTextEvents2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc5683e39da2da190468b2cafd0d3accae9b7479
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904010"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Diese Schnittstelle wird verwendet, um Visual Studio über Änderungen am Quelldokument zu benachrichtigen, die von der Debug-Engine bereitgestellt werden.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um das vornehmen von Änderungen am Quellcode zu unterstützen. Diese Schnittstelle wird in der Regel auf demselben Objekt implementiert, das die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ruft diese Schnittstelle mithilfe eines Aufrufs der- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Methode ab. Die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird von einem Aufrufder- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> Methode abgerufen. Die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle wird durch Aufrufen der [QueryInterface](/cpp/atl/queryinterface) -Methode in einer [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocumentTextEvents2` .

|Methode|Beschreibung|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt das Debugpaket, dass Text in das Dokument eingefügt wurde.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt das Debugpaket, dass der Text aus dem Dokument entfernt wurde.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt das Debugpaket, dass Text im Dokument ersetzt wurde.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt das Debugpaket, dass die Text Attribute im Dokument aktualisiert wurden.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt den Empfänger des Ereignisses, dass die Dokument Attribute aktualisiert wurden.|

## <a name="remarks"></a>Bemerkungen
 Nur Debug-engines, die eigene Dokumente bereitstellen, nutzen die- `IDebugDocumentTextEvent2` Schnittstelle. Ein Beispiel hierfür wäre eine Skript-Debug-Engine. Beim Interpretieren von Skripts kann neuer Quellcode generiert werden, der nicht in einer Datenträger Datei vorhanden ist und nur der "de" bekannt ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
