---
description: Diese Schnittstelle beschreibt ein Array Symbol oder einen Typ.
title: Idebugarrayfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3926bb47e1ea8a91289a7454f289cd3806e97f7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158721"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Diese Schnittstelle beschreibt ein Array Symbol oder einen Typ.

## <a name="syntax"></a>Syntax

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle implementiert. Diese Schnittstelle ist eine Spezialisierung, die Array Objekte darstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) das-Flag zurückgibt `FIELD_TYPE_ARRAY` .

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in den Schnittstellen [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) und [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ruft die Anzahl der Elemente im Array ab.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ruft den Typ des Elements im Array ab.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ruft den Rang des Arrays ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
