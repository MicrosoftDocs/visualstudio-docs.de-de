---
description: Diese Schnittstelle beschreibt eine-Methode.
title: Idebugmethodfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05a90252241dd51e1c567847891cf681c88d8fba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166306"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Diese Schnittstelle beschreibt eine-Methode.

## <a name="syntax"></a>Syntax

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das die [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle implementiert. Diese Schnittstelle ist eine Spezialisierung, die eine Methode darstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle abzurufen, wenn [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt `FIELD_TYPE_METHOD` . Außerdem geben die Methoden [getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [getpropertysetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)und [enumkonstruktoren](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)alle die- `IDebugMethodField` Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in den Schnittstellen [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) und [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Erstellt einen Enumerator für die Parameter der Methode.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ruft den "This"-Zeiger des Objekts ab, das die Methode enthält.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Erstellt einen Enumerator für alle lokalen Variablen der Methode.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Erstellt einen Enumerator für statische lokale Variablen der Methode.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ruft den globalen Container der Methode ab.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Erstellt einen Enumerator für den Typ jedes Arguments, das erforderlich ist, um die Methode aufzurufen.|

## <a name="remarks"></a>Bemerkungen
 Eine Methode kann sowohl Parameter als auch lokale Variablen enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
