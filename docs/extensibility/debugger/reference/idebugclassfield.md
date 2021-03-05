---
description: Diese Schnittstelle stellt eine Klasse als Typ dar.
title: Idebugclassfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c8f566d7decc344dda17700da6712ff78120a1c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164174"
---
# <a name="idebugclassfield"></a>IDebugClassField
Diese Schnittstelle stellt eine Klasse als Typ dar.

## <a name="syntax"></a>Syntax

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle implementiert. Diese Schnittstelle ist eine Spezialisierung, die einen Klassentyp darstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Eine Reihe von Schnittstellen verfügt über Methoden, die diese Schnittstelle zurückgeben können, einschließlich [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)und [idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Sie können auch [QueryInterface](/cpp/atl/queryinterface) verwenden, um diese Schnittstelle von der [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle abzurufen, wenn die [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode das-Flag zurückgibt `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in den Schnittstellen [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) und [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Erstellt einen Enumerator für die Basisklassen dieser Klasse.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Erstellt einen Enumerator für die in der Klasse aufgeführten Klassen.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ruft die Klasse ab, die diese Klasse einschließt.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Erstellt einen Enumerator für die Konstruktoren dieser Klasse.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ruft den Namen des Standardindexers ab.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Erstellt einen Enumerator für die unter aufgefügten Enumeratoren dieser Klasse.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
