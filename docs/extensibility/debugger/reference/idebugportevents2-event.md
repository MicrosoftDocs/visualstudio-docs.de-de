---
title: 'IDebugPortEvents2:: Event | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725250"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Diese Methode sendet Ereignisse, die die Erstellung und Zerstörung von Prozessen und Programmen an einem Port angeben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parameter
`pMachine`\
in Ein [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Objekt, das den debugserver darstellt (es gibt einen für jede Instanz von [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ), in dem das Ereignis aufgetreten ist.

`pPort`\
in Ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Objekt, das den Port darstellt, in dem das Ereignis aufgetreten ist.

`pProcess`\
in Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess darstellt, in dem das Ereignis aufgetreten ist.

`pProgram`\
in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, in dem das Ereignis aufgetreten ist.

`pEvent`\
in Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Objekt, das das Ereignis bezeichnet. Die möglichen Ereignisse lauten wie folgt:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
in Die GUID des Ereignisses. Da das-Ereignis vor dem Aufruf dieser Methode in [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) umgewandelt wird, erleichtert dieser Bezeichner das Ermitteln des Ereignisses, das gesendet wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
