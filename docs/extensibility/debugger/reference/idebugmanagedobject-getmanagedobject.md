---
title: 'Idebugmanagedobject:: getmanagedobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7080760b174c51d62c44cd2757944948e0104ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727737"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Gibt eine-Schnittstelle zurück, die das verwaltete-Objekt darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parameter
`ppManagedObject`\
vorgenommen Gibt eine-Schnittstelle zurück, die das verwaltete-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die von dieser Methode zurückgegebene Schnittstelle kann für jede Schnittstelle abgefragt werden, die von der verwalteten Klasse implementiert wird, sodass Ihre Methoden aufgerufen werden können.

## <a name="see-also"></a>Weitere Informationen
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
