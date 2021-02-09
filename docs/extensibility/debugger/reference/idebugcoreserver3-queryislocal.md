---
title: 'IDebugCoreServer3:: queryislocal | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad3b442382f26c1754689c005793c489b9cd5d3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923178"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Bestimmt, ob der Server für den Aufrufer lokal ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Rückgabewert
 Gibt zurück `S_OK` , um anzugeben, dass der Server lokal ist. Gibt zurück `S_FALSE` , wenn der Server von einer Instanz von msvsmon.exe ausgeführt wird, die in der Regel für das Remote Debuggen verwendet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
