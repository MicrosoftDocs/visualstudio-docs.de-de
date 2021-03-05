---
description: Ruft die Klasse ab, die diese Klasse einschließt.
title: 'Idebugclassfield:: getenclosingclass | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c08550204c8a2860d8fd7870e4ac949e9e9319c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164200"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ruft die Klasse ab, die diese Klasse einschließt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parameter
`ppClassField`\
vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das die einschließende Klasse darstellt. Gibt einen NULL-Wert zurück, wenn keine einschließende Klasse vorhanden ist.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Wenn die Klasse, die durch dieses [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt dargestellt wird, eine-Klasse ist, gibt der- `ppClassField` Parameter ein-Objekt zurück, `IDebugClassField` das die einschließende Klasse darstellt. Beispiel für diese Klassendefinition:

```
class RootClass {
    class NestedClass { }
};
```

Das Aufrufen der- `GetEnclosingClass` Methode für das- `IDebugClassField` Objekt, das die-Klasse darstellt, `NestedClass` gibt ein Objekt zurück, `IDebugClassField` das die `RootClass`

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
