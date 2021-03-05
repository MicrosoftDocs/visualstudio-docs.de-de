---
description: Gibt an, wie die Debug-Engine (de) eine bestimmte Ausnahme behandeln soll.
title: 'IDebugEngine2:: abtexception | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 543cccbbefd12accd75213f255f8e3b677cdea38
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153936"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Gibt an, wie die Debug-Engine (de) eine bestimmte Ausnahme behandeln soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parameter
`pException`\
in Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die die Ausnahme beschreibt und debuggt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein de könnte angewiesen werden, das Programm zu beenden, das eine Ausnahme bei der ersten Chance, der zweiten Gelegenheit oder überhaupt nicht auslöst.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
