---
title: 'Idebugaddress:: GetAddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853011"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Gibt eine-Struktur zurück, die ein-Objekt und seinen Speicherort innerhalb seines Bereichs oder Containers beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in, out] Eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die von dieser Methode ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur wird an diese Methode weitergegeben, die Sie dann mit den entsprechenden Informationen füllt. Wie diese Informationen interpretiert werden, hängt von der Art der zurückgegebenen Informationen und dem Symbol Handler selbst ab. Weitere Informationen finden Sie unter [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Weitere Informationen
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
