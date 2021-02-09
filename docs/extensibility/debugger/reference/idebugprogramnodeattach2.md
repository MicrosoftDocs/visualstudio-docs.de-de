---
title: IDebugProgramNodeAttach2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74a25e4eefe260dd61dc951118cdb6390a61b52d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898495"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Ermöglicht, dass ein Programmknoten über einen Versuch benachrichtigt wird, dem zugeordneten Programm anzufügen.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird in derselben Klasse implementiert, die die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle implementiert, um Benachrichtigungen über einen Anfüge Vorgang zu empfangen und die Möglichkeit zu bieten, den Anfüge Vorgang abzubrechen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie diese Schnittstelle durch Aufrufen der- `QueryInterface` Methode in einem [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt ab. Die [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode muss vor der [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen werden, um dem Programmknoten die Möglichkeit zu geben, den Anfüge Vorgang zu verhindern.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Wird an das zugeordnete Programm angefügt oder den Anfüge Vorgang an die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist die bevorzugte Alternative zum veralteten [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Methode. Alle debugengines werden immer mit der `CoCreateInstance` Funktion geladen, d. h., Sie werden außerhalb des Adressraums des Programms instanziiert, das gedebuggt wird.

 Wenn eine vorherige Implementierung der- `IDebugProgramNode2::Attach_V7` Methode einfach nur den `GUID` des Programms festlegt, der deentschlgt wird, muss nur die [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode implementiert werden.

 Wenn eine vorherige Implementierung der- `IDebugProgramNode2::Attach_V7` Methode die angegebene Rückruf Schnittstelle verwendet hat, muss diese Funktion in eine Implementierung der [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode verschoben werden, und die- `IDebugProgramNodeAttach2` Schnittstelle muss nicht implementiert werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
