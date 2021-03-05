---
description: Ruft einen Enumerator für alle Elemente des Arrays ab.
title: 'Idebugarrayobject:: getElements | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33840f3f5d5a65cf1ed929049f0b85801724a5c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158552"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ruft einen Enumerator für alle Elemente des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [ienumdebugobjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) -Objekt zurück, das das Auflisten aller Elemente ermöglicht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie als Alternative die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) -Methode und die [getelate](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) -Methode, um die Elemente zu durchlaufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
