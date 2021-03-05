---
description: Ruft einen Port von einem Port Lieferanten ab.
title: 'IDebugPortSupplier2:: getPort | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fa191b70e44684577845ab4a48c6c4f82844bce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145429"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Ruft einen Port von einem Port Lieferanten ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parameter
`guidPort`\
in GUID (Global Unique Identifier) des Ports.

`ppPort`\
vorgenommen Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Objekt zurück, das den Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_PORTSUPPLIER_NO_PORT` Wenn kein Port mit dem angegebenen Bezeichner vorhanden ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
