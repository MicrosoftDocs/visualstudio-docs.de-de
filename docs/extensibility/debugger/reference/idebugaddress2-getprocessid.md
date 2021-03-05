---
description: Ruft die ID des Prozesses ab, der das von dieser IDebugAddress2-Schnittstelle dargestellte Objekt besitzt.
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
ms.openlocfilehash: eeae55e91df8dac3fb176952a352df642facb055
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154950"
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
