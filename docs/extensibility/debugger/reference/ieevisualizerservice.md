---
title: Ieevisualizerservice | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b10a09aeab6012981fd464694c641aaf6bba4951
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842237"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle implementiert Schlüsselmethoden, die Funktionen für die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -und [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstellen bereitstellen.

## <a name="syntax"></a>Syntax

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio implementiert, damit eine Ausdrucks Auswertung (EE) typvisualisierungen unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der EE ruft " [anatevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) " auf, um diese Schnittstelle als Teil der Unterstützung für typvisualisierungen zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge

|Methode|Beschreibung|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Ruft die Anzahl der benutzerdefinierten Viewer ab, die dieser Dienst kennt.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Ruft die Liste der benutzerdefinierten Viewer ab.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Gibt ein Proxy Objekt für eine Eigenschaft zurück.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Ruft die Anzahl der Wert Zeichenfolgen ab, die für die angegebene Eigenschaft oder das angegebene Feld angezeigt werden sollen.|

## <a name="remarks"></a>Bemerkungen
 In der IDE wird die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle verwendet, um zu bestimmen, ob benutzerdefinierte Viewer oder typvisualisierungen für die Eigenschaft vorhanden sind. Durch das Erstellen eines schnell Ansichts Dienstanbieter (mit "" "" "" "" "" "" "" "" "" "" "" "," "" "" " [") "](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)," "und" " `IDebugProperty3` unterstützen typvisualisierungen. [](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

 Wenn ein EE benutzerdefinierte Viewer hat, die er implementiert, kann der EE die `CLSID` e dieser benutzerdefinierten Viewer an das Ende der von [getcustomviewerlist](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)zurückgegebenen Liste anfügen. Dies ermöglicht es einem EE, beide typvisualisierungen und ihre eigenen benutzerdefinierten Viewer zu unterstützen. Stellen Sie sicher, dass [getcustomviewercount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) das Hinzufügen von benutzerdefinierten Viewern widerspiegelt.

 Eine Erläuterung des Unterschieds zwischen Visualisierungen und Viewern finden Sie unter [typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
