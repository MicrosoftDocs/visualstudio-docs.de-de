---
description: Sendet eine Benachrichtigung über Debugereignisse.
title: 'IDebugEventCallback2:: Event | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa0cfd8f96d21a510370a4fc526a3cae053c77b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152922"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Sendet eine Benachrichtigung über Debugereignisse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Parameter
`pEngine`\
in Ein [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Objekt, das die Debug-Engine (de) darstellt, die dieses Ereignis sendet. Zum Ausfüllen dieses Parameters ist ein de erforderlich.

`pProcess`\
in Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess darstellt, in dem das Ereignis auftritt. Dieser Parameter wird vom Sitzungs-Debug-Manager (SDM) ausgefüllt. Ein de übergibt immer einen NULL-Wert für diesen Parameter.

`pProgram`\
in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, in dem dieses Ereignis auftritt. Bei den meisten Ereignissen ist dieser Parameter kein NULL-Wert.

`pThread`\
in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem dieses Ereignis auftritt. Zum Beenden von Ereignissen kann dieser Parameter kein NULL-Wert sein, da der Stapel Rahmen aus diesem Parameter abgerufen wird.

`pEvent`\
in Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Objekt, das das Debug-Ereignis darstellt.

`riidEvent`\
in GUID, die identifiziert, welche Ereignis Schnittstelle aus dem Parameter abgerufen werden soll `pEvent` .

`dwAttrib`\
in Eine Kombination von Flags aus der [eventattributenumeration](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Beim Aufrufen dieser Methode muss der- `dwAttrib` Parameter mit dem Wert identisch sein, der von der [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) -Methode zurückgegeben wird, wie für das im-Parameter übergebenen Ereignis Objekt aufgerufen `pEvent` .

 Alle Debugereignisse werden asynchron gesendet, unabhängig davon, ob ein Ereignis selbst asynchron ist. Wenn eine de diese Methode aufruft, gibt der Rückgabewert nicht an, ob das Ereignis verarbeitet wurde, sondern nur, ob das Ereignis empfangen wurde. In den meisten Fällen wurde das Ereignis nicht verarbeitet, wenn diese Methode zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
