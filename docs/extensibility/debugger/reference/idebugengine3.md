---
title: IDebugEngine3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a985acc5a949ead841239d56c8b067967531fb1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927053"
---
# <a name="idebugengine3"></a>IDebugEngine3
Stellt eine einzelne Debug-Engine (de) dar, die das Debuggen eines oder mehrerer Module steuert.

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten de implementiert (sofern Sie Symbole unterstützt), um den Status "justMyCode" zu aktivieren. Diese Schnittstelle muss von der de implementiert werden, wenn Sie Symbole und JustMyCode unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird vom Sitzungs-Debug-Manager (SDM) aufgerufen, um Benutzeroptionen für Speicherorte zu übergeben, von denen Symbole geladen werden. Sie wird auch aufgerufen, um die GUID der Engine festzulegen, wenn Sie instanziiert wird (diese GUID basiert auf den Metriken der Engine-Registrierung). Der SDM ruft auch diese Schnittstelle auf, um den Zustand "justMyCode" festzulegen und alle vom Debugger bekannten Ausnahmen auf einen angegebenen Zustand festzulegen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)geerbten Methoden macht die- `IDebugEngine3` Schnittstelle die folgenden Methoden verfügbar.

|Methode|Beschreibung|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Legt den Pfad oder die Pfade fest, die von der de für die Suche nach Debugsymbolen verwendet werden.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Lädt die Symbole für alle Module, deren Symbole noch nicht geladen wurden.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Teilt der de Informationen zu den JustMyCode-Informationen mit.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Legt die de GUID aus den Metriken fest.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Legen Sie alle aktuell ausstehenden Ausnahmen in einem angegebenen Zustand fest.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
