---
description: Informiert eine Debug-Engine (de) darüber, dass das angegebene Programm atypisch beendet wurde und dass die de alle Verweise auf das Programm bereinigen und ein Programm zerstörungsereignis senden soll.
title: IDebugEngine2::D estroyprogram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ee646b48a36a2b2c5d707eab6c5a32145d55439
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162679"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informiert eine Debug-Engine (de) darüber, dass das angegebene Programm atypisch beendet wurde und dass die de alle Verweise auf das Programm bereinigen und ein Programm zerstörungsereignis senden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parameter
`pProgram`\
in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, das atypisch beendet wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, sendet der de-Vorgang ein [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) -Ereignis zurück an den Sitzungs-Debug-Manager (SDM).

 Diese Methode ist nicht implementiert (gibt zurück `E_NOTIMPL` ), wenn die de in demselben Prozess wie das debuggerprogramm ausgeführt wird. Diese Methode wird nur implementiert, wenn die de in demselben Prozess wie die SDM ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
