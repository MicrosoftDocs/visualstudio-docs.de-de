---
description: Bestimmt, ob ein benutzerdefiniertes Attribut für dieses Feld vorhanden ist, und gibt, sofern vorhanden, die Attributinformationen zurück.
title: IDebugCustomAttributeQuery2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62461cbdbfe373f6c3d45569564e611efdd6f452
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160224"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bestimmt, ob ein benutzerdefiniertes Attribut für dieses Feld vorhanden ist, und gibt, sofern vorhanden, die Attributinformationen zurück.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) implementiert, um benutzerdefinierte Attribute zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden Sie [QueryInterface](/cpp/atl/queryinterface) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle werden die Methoden der **idebugcustomattributequery** -Schnittstelle angezeigt.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Attributinformationen für das angegebene benutzerdefinierte Attribut ab.|

 Zusätzlich zu den **idebugcustomattributequery** -Methoden `IDebugCustomAttributeQuery2` implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die an dieses Feld angefügt sind.|

## <a name="remarks"></a>Bemerkungen
 Die [ienumdebugcustomattribute](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) -Methode kann einen Enumerator für alle für dieses Feld definierten benutzerdefinierten Attribute zurückgeben.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
