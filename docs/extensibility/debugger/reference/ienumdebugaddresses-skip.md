---
title: 'Ienumdebug-Adressen:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0921d2b65aedb94c15c66ad878aa66bff73dbe2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923047"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Diese Methode überspringt die angegebene Anzahl von Elementen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Anzahl der zu überspringenden Elemente.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn `celt` größer als die Anzahl der verbleibenden Elemente ist; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn `celt` einen Wert angibt, der größer als die Anzahl der verbleibenden Elemente ist, wird die Enumeration auf das Ende festgelegt und `S_FALSE` zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
