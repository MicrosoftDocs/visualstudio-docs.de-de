---
title: 'Idebugobject:: IsEqual | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 406e93456f1bd6d92a42f1584d19aeb52dd5ff93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846776"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Vergleicht ein-Objekt mit diesem-Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parameter
`pObject`\
in Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das das Objekt darstellt, mit dem verglichen werden soll.

`pfIsEqual`\
vorgenommen Gibt einen Wert ungleich 0 (NULL `TRUE` ) zurück, wenn die Werte der-Objekte gleich sind; andernfalls wird NULL () zurückgegeben `FALSE` .

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In der Regel kann diese Methode die Adressen der durch den `pObject` -Parameter dargestellten Werte und dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt vergleichen. wenn die Adressen gleich sind, können die-Objekte als gleich betrachtet werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
