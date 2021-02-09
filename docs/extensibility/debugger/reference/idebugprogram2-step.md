---
title: 'IDebugProgram2:: Step | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 544ca22d263a3fca47f9484ac126031e83cde4e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911911"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Führt einen Schritt aus.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden Sie stattdessen die [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) -Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parameter
`pThread`\
in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den abgestuften Thread darstellt.

`sk`\
in Ein Wert aus der [stepkind](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der die Art des Schritts angibt.

`step`\
in Ein Wert aus der [stepunit](../../../extensibility/debugger/reference/stepunit.md) -Enumeration, der die Einheit des Schritts angibt (z. b. durch Anweisung oder Anweisung).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn eine Thread Synchronisierung oder Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Programm ausgeführt werden, wenn ein bestimmter Thread schrittweise ausgeführt wird.

> [!WARNING]
> Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
