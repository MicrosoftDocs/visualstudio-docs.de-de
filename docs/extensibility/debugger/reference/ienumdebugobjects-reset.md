---
title: 'Ienumdebugobjects:: Reset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39f2949a0c3b0c7009b17c8ceee09eee210c61cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957100"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Diese Methode setzt die Enumeration auf das erste Element zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf von [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) das erste Element der-Enumeration zurück.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
