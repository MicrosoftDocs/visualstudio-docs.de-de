---
title: Typvisualizer und Custom Viewer | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Typen von Visualisierungs Komponenten und die benutzerdefinierten Viewer, die Daten in einem bestimmten Format anzeigen, und die Unterschiede zwischen Ihnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac759dd245da8d803cb943dd6398d9ae642aaf23
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995940"
---
# <a name="type-visualizer-and-custom-viewer"></a>Typschnell Ansicht und benutzerdefinierter Viewer
Eine typschnell Ansicht ist eine Komponente, mit der ein Datenelement in einem bestimmten Format angezeigt wird. Das Format ist vollständig darauf fest, wer die Schnellansicht implementiert, Sie ist der Endbenutzer oder ein Drittanbieter von Visualisierungen.

 Ein benutzerdefinierter Viewer ist der Teil einer benutzerdefinierten Ausdrucks Auswertung, der ein Datenelement in einem bestimmten Format anzeigt. Dieses Format ist vollständig auf die Implementierung des benutzerdefinierten Viewers fest, was bedeutet, dass das Format dem Implementierer der Ausdrucks Auswertung (EE) entspricht.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Unterstützung für typvisualisierungen in einer Ausdrucks Auswertung
 Ein EE unterstützt typvisualisierungen, indem er eine Reihe von Schnittstellen unterstützt, auf die Visualisierungen zugreifen können: Schnittstellen wie [ieevisualizerservice](../../extensibility/debugger/reference/ieevisualizerservice.md) und [ieevisualizerdataprovider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Der EE ist jedoch nicht für die Implementierung der typschnell Ansicht selbst zuständig: der EE ermöglicht externen visualisierern lediglich den Zugriff auf die Typinformationen. Solche schnell Ansichten werden möglicherweise zusammen mit dem EE geliefert und an der entsprechenden Stelle in Visual Studio installiert, die von einem Drittanbieter oder sogar vom Endbenutzer bereitgestellt wird.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Unterstützung für benutzerdefinierte Viewer in einer Ausdrucks Auswertung
 Ein EE kann auch benutzerdefinierte Viewer unterstützen, in denen der EE selbst den Code zum Anzeigen des Datentyps bereitstellt. Ein benutzerdefinierter Viewer implementiert die [idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md) -Schnittstelle, die alle Aufgaben zum Anzeigen der Daten in einem beliebigen Format verarbeitet. der Viewer verfügt über die vollständige Kontrolle über die Anzeige und kann sogar die Daten ändern. Alle benutzerdefinierten Viewer, die von der EE bereitgestellt werden, erhalten den EE, wenn das Produkt ausgeliefert wird.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
