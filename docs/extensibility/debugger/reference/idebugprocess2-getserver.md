---
description: Ruft den Server ab, auf dem der Prozess ausgeführt wird.
title: 'IDebugProcess2:: GetServer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fba7af19093d853d227241187242a24bf9bd8cdb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169196"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Ruft den Server ab, auf dem der Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServer( 
   IDebugCoreServer2** ppServer
);
```

```csharp
int GetServer( 
   out IDebugCoreServer2 ppServer
);
```

## <a name="parameters"></a>Parameter
`ppServer`\
vorgenommen Gibt ein [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Objekt zurück, das den Server darstellt, auf dem dieser Prozess ausgeführt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mehrere Server können auf einem einzelnen Computer ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
