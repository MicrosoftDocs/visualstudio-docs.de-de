---
description: Bewirkt, dass der Prozess eine Anweisung oder eine Anweisung schrittweise durch nimmt.
title: 'IDebugProcess3:: Step | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85df970c073fa2203873733073c5b6b85cabe06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150132"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Bewirkt, dass der Prozess eine Anweisung oder eine Anweisung schrittweise durch nimmt.

> [!NOTE]
> Diese Methode sollte anstelle von [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parameter
`pThread`\
in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den abgestuften Thread darstellt.

`sk`\
in Einer der [stepkind](../../../extensibility/debugger/reference/stepkind.md) -Werte.

`step`\
in Einer der [stepunit](../../../extensibility/debugger/reference/stepunit.md) -Werte.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn eine Thread Synchronisierung oder Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Prozess ausgeführt werden, wenn ein bestimmter Thread schrittweise ausgeführt wird.

 **Warnung** Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
