---
title: 'Idebugclassfield:: enumnetstedclasses | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63b42df8181ca12da1be2aca6faf1346406b621f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877433"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Erstellt einen Enumerator für die Klassen, die in dieser Klasse eingefügt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der geschiesteten Klassen darstellt. Gibt einen NULL-Wert zurück, wenn keine Unterklassen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine Unterklassen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Jedes Element der-Enumeration ist ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das eine geschsted-Klasse beschreibt.

Eine geschachtelte Klasse ist eine Klasse, die in einer anderen Klasse definiert ist. Beispiel:

```
class RootClass {
   class NestedClass { }
};
```

Die [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Enumeration enthält ein Objekt, das die- `NestedClass` Klasse darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
