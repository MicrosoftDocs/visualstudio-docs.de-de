---
title: 'Idebugmanagedobject:: setfrommanagedobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c1f18fbfa70faf1d3da8ae785768419765dc94b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890226"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Legt den Wert der Instanz des Value-Klassen Objekts von der Instanz der Wert Klasse fest, die als Parameter bereitgestellt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parameter
`pManagedObject`\
in Eine-Schnittstelle, die das verwaltete Objekt darstellt, das den neuen Wert enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, um das verwaltete Objekt entsprechend der Darstellung durch das [idebugmanagedobject](../../../extensibility/debugger/reference/idebugmanagedobject.md) -Objekt zu ändern.

## <a name="see-also"></a>Weitere Informationen
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
