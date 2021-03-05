---
description: Stellt ein verwaltetes Array Objekt dar und ermöglicht es einer Ausdrucks Auswertung (EE), den Basis Index (untere Begrenzungen) für das Array zu bestimmen.
title: IDebugArrayObject2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e6bb73834f53e22df63682663539b5f01685b30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174123"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt ein verwaltetes Array Objekt dar und ermöglicht es einer Ausdrucks Auswertung (EE), den Basis Index (untere Begrenzungen) für das Array zu bestimmen.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Dies wird von der Managed Debug Engine (de) implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugarrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Ruft die Basis Indizes (untere Grenzen) für jeden Index ab, wenn die Anzahl der Dimensionen im Array angegeben wird.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Bestimmt, ob für das Array Basis Indizes (untere Begrenzungen) definiert sind.|

## <a name="remarks"></a>Bemerkungen
 Eine Ausdrucks Auswertung verwendet diese Schnittstelle, um verwaltete Arrays in einer Analyse Struktur darzustellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
