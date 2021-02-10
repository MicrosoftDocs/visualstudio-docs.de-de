---
title: 'Idebugclassfield:: enumbaseclasses | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8648890e030799b985a4e917be8caf85292528a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947098"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Erstellt einen Enumerator für die Basisklassen dieser Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\

vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Basisklassen darstellt. Gibt einen NULL-Wert zurück, wenn keine Basisklassen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben, S_SH_NO_BASE_CLASSES zurückgegeben, wenn keine Basisklassen vorhanden sind (und der- `ppEnum` Parameter auf einen NULL-Wert festgelegt ist); andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Basisklassen im Enumeratorobjekt werden in der Reihenfolge der unmittelbarsten (oder am meisten abgeleiteten) Basisklasse für die meisten Remote-Basisklassen angegeben. Beispielsweise mit den C++-Klassen:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Die-Enumeration würde die Basisklassen in der Reihenfolge zurückgeben `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
