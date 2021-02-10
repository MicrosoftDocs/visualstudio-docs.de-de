---
title: IDebugModule3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa655c03665c9eed54feabc5af679765b09ac0a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955520"
---
# <a name="idebugmodule3"></a>IDebugModule3
Diese Schnittstelle stellt ein Modul dar, das alternative Positionen von Symbolen und JustMyCode-Zuständen unterstützt.

## <a name="syntax"></a>Syntax

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um alternative Positionen von Symbolen zu unterstützen und mit JustMyCode-Zuständen zu arbeiten (Weitere Informationen finden Sie im [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) für eine Definition von "justMyCode").

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufrufen von [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) gibt diese Schnittstelle zurück. Der de sendet mithilfe der- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode die [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) -Schnittstelle an den Sitzungs-Debug-Manager (SDM). Außerdem gibt ein [QueryInterface](/cpp/atl/queryinterface) -Aufrufe für eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in der [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Gibt eine Liste der Pfade, die nach Symbolen durchsucht werden, und die Ergebnisse der Suche der einzelnen Pfade zurück.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Lädt und initialisiert Symbole für das aktuelle Modul.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Gibt ein Flag zurück, das angibt, ob das Modul Benutzercode darstellt.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Gibt an, ob das Modul als Benutzercode angesehen werden soll oder nicht.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ist der typische Consumer dieser Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
