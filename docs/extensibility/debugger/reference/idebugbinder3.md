---
description: Diese Schnittstelle ermöglicht den Zugriff auf Typen, Aliase und benutzerdefinierte Visualisierungs Dienste.
title: IDebugBinder3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f6be3b149450ec84158acc533230102fce5a67e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143609"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle ermöglicht den Zugriff auf Typen, Aliase und benutzerdefinierte Visualisierungs Dienste.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine implementiert diese Schnittstelle, um Aliase, benutzerdefinierte Visualisierungs Dienste und Zugriff auf Objekttyp Informationen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Eine [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle erhält diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von der [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle bereitgestellt werden, implementiert diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Ruft ein Speicher Objekt ab, das den Speicher darstellt, an den dieses-Objekt gebunden ist.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Ruft die Ausnahme ab, die diesem-Objekt zugeordnet ist (falls vorhanden).|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Ruft einen Alias anhand seines Namens ab.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Ruft ein Array aller Aliase für dieses-Objekt ab.|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ruft die Anzahl von Argument Typen ab, die diesem-Objekt zugeordnet sind.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Ruft eine Liste von Argument Typen ab, die diesem-Objekt zugeordnet sind.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ruft eine Schnittstelle zu einem schnell Ansichts Dienst ab.|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konvertiert entweder einen Objekt Speicherort oder eine 64-Bit-Speicheradresse in einen Speicher Kontext.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
