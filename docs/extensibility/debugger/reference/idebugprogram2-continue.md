---
description: 'IDebugProgram2:: Continue führt die Ausführung des Programms mit dem Status "beendet" fort. Alle vorherigen Ausführungs Zustände (z. b. ein Schritt) werden beibehalten, und die Ausführung des Programms beginnt erneut.'
title: 'IDebugProgram2:: Continue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f10d9266e8562d7ba1afed45b4b054f306bfbca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164720"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Setzt die Ausführung dieses Programms mit dem Status "beendet" fort. Alle vorherigen Ausführungs Zustände (z. b. ein Schritt) werden beibehalten, und die Ausführung des Programms beginnt erneut.

> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden Sie stattdessen die [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) -Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread` in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird für dieses Programm aufgerufen, unabhängig davon, wie viele Programme gedebuggt werden oder welches Programm das anhalteereignis generiert hat. Die Implementierung muss den vorherigen Ausführungs Zustand beibehalten (z. b. einen Schritt) und die Ausführung fortsetzen, als ob Sie vor dem Abschließen der vorherigen Ausführung nie beendet worden wäre. Das heißt, wenn ein Thread in diesem Programm einen Schritt-für-Vorgang ausgeführt hat und beendet wurde, weil ein anderes Programm angehalten wurde, und diese Methode aufgerufen wurde, muss das Programm den ursprünglichen Step-over-Vorgang beenden.

> [!WARNING]
> Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
