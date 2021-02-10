---
title: 'Idebugobject:: "abtreferencevalue" | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1df408e11803c7cd3508d1939ca6e12f046153fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953603"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Legt den Verweis Wert dieses-Objekts fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parameter
`pObject`\
in Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das den neuen Verweis Wert darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode macht dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zu einem Verweis auf den Wert des Objekts, das im- `pObject` Parameter angegeben ist, und gibt einen vorherigen Verweis zurück. Beachten Sie, dass dieses `IDebugObject` Objekt bereits ein Referenztyp sein muss.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
