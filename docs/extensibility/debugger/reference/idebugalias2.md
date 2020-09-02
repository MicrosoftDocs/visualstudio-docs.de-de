---
title: IDebugAlias2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736363"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt einen numerischen Alias für eine Variable dar und ermöglicht einer Ausdrucks Auswertung (EE) das Abrufen der Anwendungsdomäne für den Alias.

## <a name="syntax"></a>Syntax

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von der verwalteten Debug-Engine (de) implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugalias](../../../extensibility/debugger/reference/idebugalias.md) -Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Ruft den Bezeichner für die Anwendungsdomäne ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Alias ist eine Dezimalzahl in Form von Zeichen folgen, gefolgt vom #-Zeichen, z. b. 1001 #.

## <a name="requirements"></a>Anforderungen
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
