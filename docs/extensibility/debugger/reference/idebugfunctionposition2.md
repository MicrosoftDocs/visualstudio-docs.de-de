---
description: Diese Schnittstelle stellt eine abstrakte Position einer Funktion in einem Quelldokument dar.
title: IDebugFunctionPosition2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a5717023eea18060834d1beade25199d5b0c3f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165526"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Diese Schnittstelle stellt eine abstrakte Position einer Funktion in einem Quelldokument dar.

## <a name="syntax"></a>Syntax

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um die Position einer Funktion innerhalb eines Quelldokuments darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird als Teil einer [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (insbesondere einer [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur) bereitgestellt, die wiederum Teil der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur ist, die beim Erstellen eines ausstehenden halte Punkts verwendet wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugFunctionPosition2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ruft den Namen der Funktion ab, zu der diese Position relativ ist.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ruft den Offset vom Anfang der Funktion ab.|

## <a name="remarks"></a>Bemerkungen
 Die durch diese Schnittstelle dargestellte Position ist Text basiert, insbesondere eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
