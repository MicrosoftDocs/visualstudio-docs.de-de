---
title: Implementieren von typvisualisierungen und benutzerdefinierten Viewern | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Implementieren von typvisualisierungen und benutzerdefinierten Viewern, mit denen Benutzerdaten auf eine Weise anzeigen können, die aussagekräftiger ist als ein Abbild der Zahlen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc3b1f2510742e2d0656727826e5b4aeae935b6f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559900"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementieren von typvisualisierungen und benutzerdefinierten Viewern
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Typvisualisierungen und benutzerdefinierte Viewer ermöglichen Benutzern das Anzeigen von Daten eines bestimmten Typs auf eine Weise, die aussagekräftiger ist als ein einfaches hexadezimales Abbild von Zahlen. Eine Ausdrucks Auswertung (EE) kann benutzerdefinierten Viewern bestimmte Datentypen oder Variablen zuordnen. Diese benutzerdefinierten Viewer werden von EE implementiert. Der EE kann auch externe typvisualisierungen unterstützen, die von einem anderen Drittanbieter oder sogar vom Endbenutzer stammen können.

## <a name="discussion"></a>Diskussion

### <a name="type-visualizers"></a>Typvisualisierungen
 Visual Studio fordert eine Liste der typvisualisierungen und benutzerdefinierten Viewer für jedes Objekt an, das in einem Überwachungs Fenster angezeigt werden soll. Eine Ausdrucks Auswertung (EE) liefert eine solche Liste für jeden Typ, für den typvisualisierungen und benutzerdefinierte Viewer unterstützt werden sollen. Aufrufe von [getcustomviewercount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [getcustomviewerlist](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) starten den gesamten Prozess des Zugriffs auf typvisualisierungen und benutzerdefinierte Viewer (Weitere Informationen zur Aufruf Sequenz finden Sie unter [visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md) ).

### <a name="custom-viewers"></a>Benutzerdefinierte Viewer
 Benutzerdefinierte Viewer werden in der EE für einen bestimmten Datentyp implementiert und durch die [idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md) -Schnittstelle dargestellt. Ein benutzerdefinierter Viewer ist nicht so flexibel wie eine typschnell Ansicht, da er nur verfügbar ist, wenn der EE, der diesen speziellen benutzerdefinierten Viewer implementiert, ausgeführt wird. Das Implementieren eines benutzerdefinierten Viewers ist einfacher als das Implementieren von Unterstützung für typvisualisierungen. Die Unterstützung von typvisualisierungen bietet den Endbenutzern jedoch maximale Flexibilität bei der Visualisierung Ihrer Daten. Der Rest dieser Diskussion betrifft nur typvisualisierungen.

## <a name="interfaces"></a>Schnittstellen
 Der EE implementiert die folgenden Schnittstellen zur Unterstützung von typvisualisierungen, die von Visual Studio verwendet werden können:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  Der EE verwendet die folgenden Schnittstellen zur Unterstützung von typvisualisierungen:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Siehe auch
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
