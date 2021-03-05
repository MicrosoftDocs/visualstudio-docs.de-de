---
description: Diese Methode ruft die debugadresse eines Felds ab.
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
ms.openlocfilehash: bda569ecc278fa0ff4a479b55817cd905ca85c40
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152064"
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
