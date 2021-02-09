---
title: 'Ienumdebug-Adressen:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5faba8562363d5f84cdf5cbe6dafff2aa71a0a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897110"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Diese Methode gibt den nächsten Satz von Elementen aus der-Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe des `rgelt` Arrays an.

`rgelt`\
[in, out] Array von [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Elementen, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Gibt die Anzahl der Elemente zurück, die tatsächlich in zurückgegeben werden `rgelt` .

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden kann. andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
