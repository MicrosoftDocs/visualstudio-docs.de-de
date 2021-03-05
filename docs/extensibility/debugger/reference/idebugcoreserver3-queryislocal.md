---
description: Bestimmt, ob der Server für den Aufrufer lokal ist.
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
ms.openlocfilehash: 61cb67fd350fe74f12b69596675e009b01794ef4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163069"
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
