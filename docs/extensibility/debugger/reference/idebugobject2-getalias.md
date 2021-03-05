---
description: Ruft den Alias ab, der diesem-Objekt zugeordnet ist, sofern vorhanden.
title: 'IDebugObject2:: getalias | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c2ac683a5fb4d694b7cf3ab84849b9d7c7df7a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143128"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ruft den Alias ab, der diesem-Objekt zugeordnet ist, sofern vorhanden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parameter
`ppAlias`\
vorgenommen Gibt ein [idebugalias](../../../extensibility/debugger/reference/idebugalias.md) -Objekt zurück, das den Alias für dieses Objekt darstellt. Andernfalls wird ein NULL-Wert zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Alias für ein Objekt wird mit einem Aufrufen der Methode " [kreatealias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) " erstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
