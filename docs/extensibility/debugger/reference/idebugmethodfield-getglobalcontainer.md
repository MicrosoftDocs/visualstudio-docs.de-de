---
description: Ruft den globalen Container der Methode ab.
title: 'Idebugmethodfield:: getglobalcontainer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb20551d39f3e876a836ac42906ad9c50e3c6419
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166293"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ruft den globalen Container der Methode ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parameter
`ppClass`\
vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das das Modul darstellt, in dem diese Methode definiert ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das zurückgegebene [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt stellt das gesamte Modul dar und ist ein künstliches Objekt, d. h., das Modul selbst hat keine tatsächliche Klasse, kann jedoch durch ein Objekt dargestellt werden `IDebugClassField` , sodass die verschiedenen Elemente des Moduls aufgezählt und ermittelt werden können.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
