---
description: Ruft eine Beschreibung des Computers ab, auf dem der Core-Server ausgeführt wird.
title: 'IDebugCoreServer2:: getmachineingefo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9fd7f42816ce477af4ae259adca49e8aac20137d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163212"
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Ruft eine Beschreibung des Computers ab, auf dem der Core-Server ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMachineInfo( 
   MACHINE_INFO_FIELDS Fields,
   MACHINE_INFO*       pMachineInfo
);
```

```csharp
int GetMachineInfo( 
   enum_ MACHINE_INFO_FIELDS  Fields,
   MACHINE_INFO[]             pMachineInfo
);
```

## <a name="parameters"></a>Parameter
`Fields`\
in Eine Kombination von Flags aus der [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Enumeration, die angeben, welche Felder von `pMachineInfo` ausgefüllt werden sollen.

 `pMachineInfo`\

 [in, out] Eine [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) -Struktur, die mit einer Beschreibung des Computers ausgefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
