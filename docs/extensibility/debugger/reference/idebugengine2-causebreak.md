---
title: 'IDebugEngine2:: causeelbreak | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40fd243fa8f3f67786b862c3e0cdbfd81373a53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899018"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Fordert an, dass alle Programme, die von dieser Debug-Engine (de) debuggt werden, die Ausführung bei der nächsten Ausführung eines Threads abbrechen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist asynchron: ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Ereignis wird gesendet, wenn das Programm das nächste Mal versucht, die Ausführung auszuführen, nachdem diese Methode aufgerufen wurde.

## <a name="see-also"></a>Weitere Informationen
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
