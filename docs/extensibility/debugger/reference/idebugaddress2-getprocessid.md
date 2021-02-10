---
title: 'IDebugAddress2:: GetProcessID | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 493f2476eef1cdb68f825240fa4b56779ef7a0d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944868"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Ruft die ID des Prozesses ab, der das von dieser [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) -Schnittstelle dargestellte Objekt besitzt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Parameter
`pProcID`\
vorgenommen Die Prozess-ID.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
