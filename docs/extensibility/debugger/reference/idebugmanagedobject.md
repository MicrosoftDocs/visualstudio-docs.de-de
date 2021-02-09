---
title: Idebugmanagedobject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90540aaf5f7e409c8fc7fa44126f195230317f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929809"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle ermöglicht es der Ausdrucks Auswertung (EE), Eigenschaften oder Methoden für Wert Klassen Instanzen (z. b.) aufzurufen `System.Decimal` und um ihren Wert festzulegen, ohne die [Auswertung](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) für das Programm aufzurufen, das gedeppt wird.

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Ausdrucks Auswertung implementiert diese Schnittstelle, um ein verwaltetes Code Objekt, z. b. eine Variable, darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Um diese Schnittstelle zu erhalten, rufen Sie [getmanageddebugobject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) für ein [idebugobject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) auf, das eine Instanz einer Value-Klasse darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md)geerbt werden, stellt die- `IDebugManagedObject` Schnittstelle die folgenden Methoden zur Verfügung.

|Methode|Beschreibung|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Gibt eine-Schnittstelle zurück, die das verwaltete Code Objekt darstellt und von dem eine beliebige entsprechende verwaltete Code Schnittstelle abgerufen werden kann.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Legt den Wert dieses-Objekts auf den Wert eines angegebenen verwalteten Code Objekts fest.|

## <a name="remarks"></a>Bemerkungen
 Eine Ausdrucks Auswertung verwendet diese Schnittstelle, um ein verwaltetes Code Objekt in einer Analyse Struktur zu speichern.

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Evaluieren](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
