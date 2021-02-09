---
title: Ieevisualizerdataprovider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 726ae6c0f56f177a6baa6f463e843378fdc0acea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890824"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet die Möglichkeit, den Wert eines Objekts über eine typschnell Ansicht zu ändern.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Ausdrucks Auswertung implementiert diese Schnittstelle, um das Ändern von Daten in einem Eigenschafts Objekt über eine typschnell Ansicht zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird verwendet, um das [ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md) -Objekt durch einen Aufrufen von " [anatevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)" zu erstellen. Weitere Informationen finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge

|Methode|Beschreibung|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bestimmt, ob es möglich ist, das Objekt (und danach seinen Wert) zu aktualisieren, das diese Schnellansicht darstellt.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Erzwingt eine erneute Auswertung des-Objekts für diese Schnellansicht.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ruft ein vorhandenes-Objekt für diese Schnellansicht ab (keine Auswertung erfolgt).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualisiert das-Objekt für diese Schnellansicht und ändert dadurch den Wert, den die Schnellansicht darstellt.|

## <a name="remarks"></a>Bemerkungen
 Der schnell Ansichts Dienst (wie durch die [ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md) -Schnittstelle dargestellt und von " [deevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)" zurückgegeben) speichert einen Verweis auf das Objekt, das die- `IEEVisualizerDataProvider` Schnittstelle implementiert. Folglich sollte die- `IEEVisualizerDataProvider` Schnittstelle nicht für das gleiche Objekt implementiert werden, das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, wenn dieses Objekt einen Verweis auf das Objekt beibehält `IEEVisualizerService` : ein Zirkel Verweis Ergebnis und ein Deadlock treten auf, wenn die Objekte zerstört werden. Die empfohlene Vorgehensweise ist die Implementierung `IEEVisualizerDataProvider` von für ein separates Objekt, an das das `IDebugProperty2` Objekt delegiert, ohne dass es aufgerufen wird `IUnknown::AddRef` .

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
