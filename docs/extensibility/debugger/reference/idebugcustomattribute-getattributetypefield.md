---
title: 'Idebugcustomattribute:: getattributetypefield | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fa72b6dfc02f29e5efd8d3e04f98f078cba66a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928444"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Ruft den Typ der benutzerdefinierten Attribut Klasse ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>Parameter
`ppCAType`\
vorgenommen Gibt das [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das die Klasse darstellt, von der das benutzerdefinierte Attribut eine Instanz ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode ermöglicht den Zugriff auf ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das diese Klasse beschreibt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
