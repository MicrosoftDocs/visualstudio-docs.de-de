---
title: 'Idebugclassfield:: enumberstedenums | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9c283d4b07458368a4ea5f143dc83bf13453302
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912010"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Erstellt einen Enumerator für die unter aufgefügten Enumeratoren dieser Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der geschiesteten Enumerationen darstellt. Gibt einen NULL-Wert zurück, wenn keine unter aufgefügten Enumerationen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine unter-Enumeratoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Jedes Element der-Enumeration ist ein [idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) -Objekt, das eine geschsted-Enumeration beschreibt.

Eine Enumeration, die innerhalb einer Klasse deklariert wird, wird als geschachtelte Enumeration betrachtet. Angenommen, dies liegt vor:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Die- `EnumNestedEnums` Methode gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das ein [idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) -Objekt enthält, das die- `NestedEnum` Enumeration darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
