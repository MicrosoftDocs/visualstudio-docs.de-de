---
title: Idebugcustomattribute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732678"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Diese Schnittstelle stellt ein benutzerdefiniertes Attribut dar und kann den Namen, das übergeordnete Element und den Klassentyp des Attributs bereitstellen.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle, um benutzerdefinierte Attribute zu unterstützen, die mit einem Symbol verknüpft sind. Sie wird in der Regel auf einem eigenen Objekt implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Bei einem [nächsten](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) -Befehl wird diese Schnittstelle zurückgegeben. Ein Aufrufen der [enumcustomattributormethode](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) gibt die [ienumdebugcustomattribute](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) -Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugCustomAttribute` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ruft das Feld ab, an das das aktuelle Attribut angefügt wird.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ruft den Typ der benutzerdefinierten Attribut Klasse ab.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ruft den Namen des benutzerdefinierten Attributs ab.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ruft die Attributinformationen als ein BLOB von Bytes ab.|

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefiniertes Attribut ist eine Struktur für c#, die benutzerdefinierte Metadaten bereitstellt, die einer bestimmten Klasse oder Methode zugeordnet sind.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
