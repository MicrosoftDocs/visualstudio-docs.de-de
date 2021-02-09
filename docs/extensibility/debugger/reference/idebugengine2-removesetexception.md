---
title: 'IDebugEngine2:: removesetexception | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29756b3be6d2c46d39b581dd3db0af61bfaa18f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878928"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Entfernt die angegebene Ausnahme, sodass Sie nicht mehr von der Debug-Engine verarbeitet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parameter
`pException`\
in Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die die zu entfernende Ausnahme beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Ausnahme, die entfernt wird, muss zuvor durch einen früheren Aufrufen der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) -Methode festgelegt worden sein.

 Um alle festgelegten Ausnahmen gleichzeitig zu entfernen, müssen Sie die [removeallsetexceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
