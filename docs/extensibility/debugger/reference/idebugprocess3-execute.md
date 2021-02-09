---
title: 'IDebugProcess3:: Execute | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4a697a4677b6bedef376e602c4327dff66ead53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915416"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Setzt die Ausführung dieses Prozesses mit dem Status "beendet" fort. Alle vorherigen Ausführungs Zustände (z. b. ein Schritt) werden gelöscht, und der Prozess beginnt erneut mit der Ausführung.

> [!NOTE]
> Diese Methode sollte anstelle von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread`\
in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den auszuführenden Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Benutzer die Ausführung von einem beendeten Zustand in einem anderen Prozess Thread startet, wird diese Methode für diesen Prozess aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer den Befehl **Start** im Menü **Debuggen** in der IDE auswählt. Die Implementierung dieser Methode kann so einfach sein wie das Aufrufen der [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) -Methode für den aktuellen Thread im Prozess.

> [!WARNING]
> Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
