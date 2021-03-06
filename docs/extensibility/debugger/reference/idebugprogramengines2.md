---
description: Diese Schnittstelle wird von Programmknoten verwendet, um alle möglichen debugengines (de) anzugeben, die das Programm debuggen können.
title: IDebugProgramEngines2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c19b4dc3967cf7001144d38114a1f873776cb2b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149586"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Diese Schnittstelle wird von Programmknoten verwendet, um alle möglichen debugengines (de) anzugeben, die das Programm debuggen können.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein de oder ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle für das gleiche Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um die Einrichtung eines bestimmten de für ein bestimmtes Programm zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugProgramNode2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramEngines2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Gibt alle möglichen des an, mit denen das Programm debuggt werden kann.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wählt den de aus, der zum Debuggen dieses Programms verwendet wird.|

## <a name="remarks"></a>Bemerkungen
 Nachdem eine de vom Benutzer ausgewählt wurde, wird diese Auswahl beim Programmknoten [durch Aufrufen von](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)"" auf "" festgelegt. Die ausgewählte Engine wird zur Engine, die von [getengineinfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
