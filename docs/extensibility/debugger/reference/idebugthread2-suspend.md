---
title: 'IDebugThread2:: Suspend | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ede08dfd2c5f8ee3a205f744388d9aac3f8f3709
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893658"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Hält einen Thread an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parameter
`pdwSuspendCount`\
vorgenommen Gibt den anhaltezähler nach dem Anhaltevorgang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jeder Aufrufe dieser Methode erhöht den anhaltezähler über 0. Diese anhalteanzahl wird im Fenster **Threads** Debuggen angezeigt.

 Für jeden Aufrufe dieser Methode muss ein späterer aufrufbedarf an der [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) -Methode vorhanden sein.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)
