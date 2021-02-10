---
title: Idebugenenfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a67c660ec8457191e688fdd430c3f7a07b5d75c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933322"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Diese Schnittstelle stellt einen Enumerationstyp dar.

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle, um eine Enumeration darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den Methoden der `IDebugField` -Schnittstelle und der- `IDebugContainerField` Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen für diesen Enumerationstyp beschreibt.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Gibt den Namen der Enumerationskonstante zurück, die dem angegebenen Wert zugeordnet ist.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Gibt den Wert zurück, der dem angegebenen enumerationskonstantennamen zugeordnet ist|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Gibt den Wert zurück, der dem angegebenen Namen der Enumerationskonstante zugeordnet ist|

## <a name="remarks"></a>Bemerkungen
 Dabei handelt es sich um das zugrunde liegende Symbol, das tatsächlich an einen Speicherort mit [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)gebunden ist.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)
