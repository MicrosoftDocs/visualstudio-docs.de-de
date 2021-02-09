---
title: Idebugarrayobject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83d6a37a5b83cd71123521db70920fd3d454e059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870063"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Array Objekt dar.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Ausdrucks Auswertung implementiert diese Schnittstelle, um ein Array darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle kann diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface) abrufen, wenn das Objekt ein Array darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden der- `IDebugObject` Schnittstelle werden die folgenden Methoden für die- `IDebugArrayObject` Schnittstelle implementiert.

|Methode|Beschreibung|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ruft die Anzahl der Elemente im Array ab.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ruft ein Element des-Arrays ab.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ruft alle Elemente des Arrays ab.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ruft den Rang des Arrays ab.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ruft die Dimensionen des Arrays ab.|

## <a name="remarks"></a>Bemerkungen
 Eine Ausdrucks Auswertung verwendet diese Schnittstelle zur Darstellung von Arrays in einer Analyse Struktur.

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
