---
title: 'Idebugobject:: isread Only | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e7d27e6a437c46d2ee72eb4fd5f79eaa9e912ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953629"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Bestimmt, ob dieses-Objekt schreibgeschützt ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parameter
`pfIsReadOnly`\
vorgenommen Gibt einen Wert ungleich 0 (NULL `TRUE` ) zurück, wenn dieses-Objekt schreibgeschützt ist; andernfalls wird NULL () zurückgegeben `FALSE` .

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Schreib geschütztes Objekt kann seinen Wert nicht ändern, nachdem es erstellt wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
