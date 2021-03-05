---
description: Diese Schnittstelle registriert oder hebt die Registrierung eines Programms auf, das mit dem Port, auf dem er ausgeführt wird, deentschlbelt werden kann.
title: IDebugPortNotify2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 759be0ff57da7c6bb65ed6ca8191720f835b894a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169339"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Diese Schnittstelle registriert oder hebt die Registrierung eines Programms auf, das mit dem Port, auf dem er ausgeführt wird, deentschlbelt werden kann.

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen vom Port zu unterstützen. Sie wird in der Regel auf demselben Objekt implementiert, das die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein [QueryInterface](/cpp/atl/queryinterface) -Rückruf für die `IDebugPort2` Schnittstelle gibt diese Schnittstelle zurück. Außerdem gibt ein Aufrufen von [getportnotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) diese Schnittstelle zurück. Eine Debug-Engine kann diese Schnittstelle als Parameter für [watchforproviderevents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)sehen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortNotify2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das mit dem Port, auf dem er ausgeführt wird, dedeentschlbelt werden kann.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung eines Programms auf, das von dem Port, auf dem er ausgeführt wird, deentschlbelt werden kann.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Debugport nicht weiß, wann Programme geladen oder entladen werden, muss ein benutzerdefinierter Port Lieferant diese Schnittstelle implementieren. Alle Programme, die für das Debuggen über einen bestimmten Port geladen werden, werden über diese Schnittstelle nachverfolgt.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
