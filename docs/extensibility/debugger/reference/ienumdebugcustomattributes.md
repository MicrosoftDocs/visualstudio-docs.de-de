---
description: Listet benutzerdefinierte Attribute auf.
title: Ienumentbugcustomattribute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bffa799ba14738daea480a1677f1b1a820e98767
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226838"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Listet benutzerdefinierte Attribute auf.

## <a name="syntax"></a>Syntax

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle, um benutzerdefinierte Attribute (über die [idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) -Schnittstelle) zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
- [Enumcustomattribute](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugCustomAttributes` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Ruft eine angegebene Anzahl von benutzerdefinierten Attributen in einer enumerationssequenz ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Überspringt eine angegebene Anzahl von benutzerdefinierten Attributen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Ruft die Anzahl der benutzerdefinierten Attribute in einem Enumerator ab.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
