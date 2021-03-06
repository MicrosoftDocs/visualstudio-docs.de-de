---
description: Diese Methode überspringt die angegebene Anzahl von Elementen in der Enumeration der Adressen.
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
ms.openlocfilehash: 1ae1b23c28f98d90649e701b7ff96b2394a9894b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222652"
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
