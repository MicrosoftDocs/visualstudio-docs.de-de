---
title: Ausdrucks Bewertungs Schnittstellen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a048d11b09ee873a2f5a11e35db78f68df6ad680
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936937"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Im folgenden finden Sie die Ausdrucks Evaluierungs Schnittstellen für das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debuggingsdk.

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden verwendet, um Ausdrücke in einer-Rückruf Stapel während des Break-Modus auszuwerten. Sie werden nur für Common Language Run-Time Expression Auswertungen (EE) implementiert.

 Jede Schnittstelle in der Tabelle zeigt die Komponente an, die Sie aus der folgenden Liste implementieren kann:

- Debug-Engine (de)

- Ausdrucks Auswertung (EE)

- Visual Studio (VS)

|Schnittstelle|Implementiert von|Beschreibung|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Stellt einen numerischen Alias für eine Variable dar.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Stellt einen numerischen Alias für eine Variable dar und ermöglicht einer Ausdrucks Auswertung (EE) das Abrufen der Anwendungsdomäne für den Alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Stellt ein Arrayobjekt dar.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Stellt ein verwaltetes Array Objekt dar und ermöglicht es einer Ausdrucks Auswertung (EE), den Basis Index (untere Begrenzungen) für das Array zu bestimmen.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Stellt einen Binder dar, der Debugsymbole an tatsächliche Adressen im Arbeitsspeicher bindet.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identisch mit der [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, bietet aber Zugriff auf Typen, Aliase und benutzerdefinierte Visualisierungen.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Stellt die Ausdrucksauswertung dar.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Stellt eine erweiterte Version einer Ausdrucks Auswertung (EE) dar.|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Stellt eine Ausdrucks Auswertung (EE) mit einer erweiterten Parserstruktur dar.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Stellt eine Funktion dar.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Stellt eine Funktion dar und erweitert die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Ermöglicht es einer Ausdrucks Auswertung (EE), eine Meldung im Ausgabefenster des Debuggers anzuzeigen.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Stellt ein verwaltetes Code Objekt dar.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Basisschnittstelle, die ein beliebiges Symbol darstellt, das an eine Speicheradresse gebunden ist.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identisch mit der [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, bietet aber Zugriff auf zusätzliche Informationen.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Stellt einen analysierten Ausdruck dar, der für die Auswertung bereit ist.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Stellt einen Zeiger dar.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Stellt einen Zeiger in einer Analyse Struktur dar und erweitert die **idebugpointerobject** -Schnittstelle.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bietet die Möglichkeit, den Wert eines Typs über eine typschnell Ansicht zu ändern.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Ermöglicht den Zugriff auf benutzerdefinierte Viewer und typvisualisierungen.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bietet die Möglichkeit, ein [ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md) -Objekt zu erstellen.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Stellt eine Auflistung von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten dar.|

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Schreiben einer CLR-Ausdrucksauswertung](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
