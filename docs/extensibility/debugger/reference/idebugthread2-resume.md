---
description: Nimmt die Ausführung eines Threads wieder auf.
title: 'IDebugThread2:: Resume | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64a7d5509ac098f6b3a47c3606b6ec530bb6b65b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164499"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Nimmt die Ausführung eines Threads wieder auf.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parameter
`pdwSuspendCount`\
vorgenommen Gibt den anhaltezähler nach dem Wiederaufnahme Vorgang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jeder Aufruf dieser Methode verringert den anhaltezähler, bis er 0 erreicht, wenn die Ausführung tatsächlich fortgesetzt wird. Diese anhalteanzahl wird im Fenster **Threads** Debuggen angezeigt.

 Für jeden Aufrufe dieser Methode muss ein vorheriger aufrufungs Vorgang der [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) -Methode vorhanden sein. Der Unterbrechungs Zähler bestimmt, wie oft die `IDebugThread2::Suspend` Methode bisher aufgerufen wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Angehalten](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
