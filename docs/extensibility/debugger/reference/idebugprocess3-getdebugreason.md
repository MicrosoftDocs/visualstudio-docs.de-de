---
title: 'IDebugProcess3:: getdebugreason | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45b51d90ec1d1c67ea722d2877e06c2a8d0d2745
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915394"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Diese Methode gibt den Grund zurück, warum der Prozess zum Debuggen gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

## <a name="parameters"></a>Parameter
`pReason`\
vorgenommen Gibt einen Wert aus der [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)
