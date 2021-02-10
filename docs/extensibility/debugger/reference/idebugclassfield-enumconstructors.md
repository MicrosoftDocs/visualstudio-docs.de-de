---
title: 'Idebugclassfield:: enumkonstruktors | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05226572d7f1b708745887338c654674e71d0f5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947081"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Erstellt einen Enumerator für die Konstruktoren für diese Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`cMatch`\
in Ein Wert aus der [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) Enumeration, der den Typ der aufzuzählungs Konstruktoren angibt.

`ppEnum`\
vorgenommen Gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Konstruktoren darstellt. Gibt einen NULL-Wert zurück, wenn keine Konstruktoren vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine Konstruktoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element der-Enumeration ist ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt, das eine Konstruktormethode beschreibt.

 Die Liste der Konstruktoren schließt in der Regel nicht die Standardkonstruktoren ein, die von einem Compiler bereitgestellt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
