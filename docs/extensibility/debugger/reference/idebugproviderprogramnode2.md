---
description: Diese Schnittstelle Marshalls programmbezogene Schnittstellen über Prozess Grenzen hinweg.
title: IDebugProviderProgramNode2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a615c076fd34d7bc230efb0f36683b7167b66566
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167853"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Diese Schnittstelle Marshalls programmbezogene Schnittstellen über Prozess Grenzen hinweg.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle für das gleiche Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um das Marshalling von Schnittstellen über Prozess Grenzen hinweg zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugProgramNode2` Schnittstelle auf, um diese Schnittstelle zu erhalten. Wenn diese Schnittstelle nicht abgerufen werden kann, unterstützt das ' de ' kein Marshalling von-Schnittstellen.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ruft eine angegebene Schnittstelle über Prozess Grenzen ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird implementiert, wenn die de in einem separaten Prozessbereich des Programms ausgeführt wird, das gedebuggt wird, z. b., wenn die "de" im Visual Studio-Prozessbereich statt des Prozess Raums des Programms ausgeführt wird, das gedebuggt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
