---
title: Idebugpointerfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9904f02183da73df496e858fa8a81e5290a8950c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877394"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Diese Schnittstelle stellt einen Zeigertyp dar.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Symbol Anbieter implementiert diese Schnittstelle, um einen Zeiger darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den Methoden der `IDebugField` -Schnittstelle und der- `IDebugContainerField` Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das das Ziel des Zeigers beschreibt.|

## <a name="remarks"></a>Bemerkungen
 In C/C++ kann ein Zeiger ein Container sein, wenn er mit der Array Notation verwendet wird. Hat z. b `char *pString` `pString` . einen Typ von Zeiger auf `char` . `pString[3]` weist den Typ eines Containers auf, bei dem es sich um einen Zeiger auf handelt, der auf `char` das vierte Element dieses Containers verweist.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
