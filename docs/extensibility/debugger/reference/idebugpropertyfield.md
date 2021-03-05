---
description: Diese Schnittstelle stellt die Funktionen bereit, die das erhalten und Festlegen einer Eigenschaft ermöglichen.
title: Idebugpropertyfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 097d73485773052afa1e9852293211084a225099
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167905"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Diese Schnittstelle stellt die Funktionen bereit, die das erhalten und Festlegen einer Eigenschaft ermöglichen.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das das [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md)implementiert. Diese Schnittstelle ist eine Spezialisierung, die das Konzept der Eigenschaften in einer Klasse unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) -Schnittstelle abzurufen, wenn die [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode zurückgibt `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in den Schnittstellen [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) und [idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ruft die Methode ab, die die Eigenschaft abruft.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ruft die Methode ab, die die-Eigenschaft festlegt.|

## <a name="remarks"></a>Bemerkungen
 Eine Eigenschaft ist ein verwaltetes Code Konzept und stellt eine Methode dar, die als Variable behandelt wird. Eigenschaften sind in nicht verwaltetem C++ nicht vorhanden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
