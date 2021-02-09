---
title: 'IDebugEngineProgram2:: stoppt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6013770e3a334e7924cafe4563d437d4f7730bfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892683"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Beendet alle Threads, die in diesem Programm ausgeführt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird aufgerufen, wenn dieses Programm in einer Umgebung mit mehreren Programmen deentschlgt wird. Wenn ein anhalteereignis von einem anderen Programm empfangen wird, wird diese Methode für dieses Programm aufgerufen. Die Implementierung dieser Methode muss asynchron sein. Das heißt, dass nicht alle Threads beendet werden müssen, bevor diese Methode zurückgegeben wird. Die Implementierung dieser Methode kann so einfach wie das Aufrufen der [causetbreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) -Methode für dieses Programm sein.

 Implementierer sollten eine [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) senden, wenn das Programm beendet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
