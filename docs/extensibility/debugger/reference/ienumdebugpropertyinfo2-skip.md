---
title: 'IEnumDebugPropertyInfo2:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Skip
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Skip
ms.assetid: 0366c778-18eb-4065-a452-64b70c751a58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9232e5b519097312df5e54898d168bcbf07a53ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869582"
---
# <a name="ienumdebugpropertyinfo2skip"></a>IEnumDebugPropertyInfo2::Skip
Überspringt die angegebene Anzahl von Elementen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Skip(
   ULONG celt
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
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
