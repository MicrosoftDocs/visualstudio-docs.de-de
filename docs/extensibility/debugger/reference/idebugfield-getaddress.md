---
title: 'Idebugfield:: GetAddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5939f0ffd3a975c5fd3286045573fbf0da8006e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915431"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Diese Methode ruft die debugadresse eines Felds ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAddress( 
   IDebugAddress** ppAddress
);
```

```csharp
int GetAddress(
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parameter
`ppAddress`\
vorgenommen Gibt die Adresse als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurück `S_OK` gegeben; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
