---
title: Idebugfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67a5bfe92547738a672cb6881234ae80f76aeda8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869764"
---
# <a name="idebugfield"></a>IDebugField
Diese Schnittstelle stellt ein Feld dar, d. h. eine Beschreibung eines Symbols oder Typs.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle als Basisklasse für alle Felder.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle ist die Basisklasse für alle Felder. Basierend auf dem Rückgabewert von [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md)kann diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface)weitere spezialisierte Schnittstellen zurückgeben. Außerdem geben viele Schnittstellen `IDebugField` Objekte aus verschiedenen Methoden zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugField` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft Informationen über das Symbol oder den Typ ab.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Typ des Felds ab.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe eines Felds in Bytes ab.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft erweiterte Informationen zu einem Feld ab.|
|[Gleich](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft typunabhängige Informationen über das Symbol oder den Typ ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Typ entspricht der Programmiersprache C `typedef` .

 Im folgenden Beispiel für die C++-Sprache `weather` ist ein Klassentyp, und `sunny` und `stormy` sind Symbole:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Gibt an, ob ein Feld ein Symbol oder einen Typ darstellt, indem [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) aufgerufen und das [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Ergebnis überprüft wird. Wenn das- `FIELD_KIND_TYPE` Bit festgelegt ist, ist das Feld ein-Typ, und wenn das- `FIELD_KIND_SYMBOL` Bit festgelegt ist, ist es ein Symbol.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
