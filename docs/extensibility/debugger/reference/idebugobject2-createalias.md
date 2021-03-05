---
description: Erstellt eine eindeutige ID oder einen Alias für dieses Objekt oder gibt einen vorhandenen Alias zurück.
title: 'IDebugObject2:: kreatealias | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2c0059b7b3b12b8e2e59524939c4a47aad97219
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170185"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Erstellt eine eindeutige ID oder einen Alias für dieses Objekt oder gibt einen vorhandenen Alias zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parameter
`ppAlias`\
vorgenommen Der neue (oder vorhandene) Alias.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Alias ist eine Bezeichnung, die ein bestimmtes Objekt darstellt, während sich das Objekt im Arbeitsspeicher befindet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
