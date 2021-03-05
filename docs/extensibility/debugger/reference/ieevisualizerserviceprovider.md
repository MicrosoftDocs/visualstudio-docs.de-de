---
description: Diese Schnittstelle ermöglicht den Zugriff auf eine Methode, mit der ein schnell Ansichts Dienst erstellt werden kann, der zum Verarbeiten von Aufgaben für die typschnell Ansicht der IDE verwendet wird.
title: Ieevisualizerserviceprovider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d4fc53ae13588a0e285e4a62691da4d88a94d5f5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227176"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle ermöglicht den Zugriff auf eine Methode, mit der ein schnell Ansichts Dienst erstellt werden kann, der zum Verarbeiten von Aufgaben für die typschnell Ansicht der IDE verwendet wird.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio implementiert, um ein Dienst Objekt für die Schnellansicht zu erstellen, das wiederum zum Bereitstellen von Klassen-IDs `CLSID` vom Typ "schnell Ansichten" an die Visual Studio-IDE verwendet wird.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die Ausdrucks Auswertung (EE) ruft [geteeservice](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Erstellt den schnell Ansichts Dienst.|

## <a name="remarks"></a>Bemerkungen
 Die- `IEEVisualizerServiceProvider` Schnittstelle wird während der Implementierung von [evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)abgerufen. Der schnell Ansichts Dienst, der von dieser Schnittstelle erstellt wird, wird verwendet, um Funktionen für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle bereitzustellen, die für die Implementierung verantwortlich ist. Der EE ist auch dafür verantwortlich, eine [ieevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle zu implementieren, die es typvisualisierungen ermöglicht, den Wert einer Eigenschaft anzuzeigen und zu ändern.

 Ausführliche Informationen dazu, wie diese Schnittstellen interagieren, finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
