---
description: Ruft den this-Zeiger (Me in Visual Basic) des-Objekts ab, das die-Methode enthält.
title: 'Idebugmethodfield:: GetThis | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3eb303a7e0a4795d3f7ef49f9114cc942bff9b2d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164941"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ruft den `this` ( `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] )-Zeiger des-Objekts ab, das die-Methode enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parameter
`ppClass`\
vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das den "This"-Zeiger darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In objektorientierten Sprachen gibt es in der Regel einen impliziten Zeiger auf die aktuelle Instanziierung einer Klasse. Dies wird `this` in c#/C + + und as in als `Me` bezeichnet [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
