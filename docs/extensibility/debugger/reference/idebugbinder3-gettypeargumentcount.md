---
description: Diese Methode gibt die Anzahl von Argument Typen zurück, die diesem-Objekt zugeordnet sind.
title: 'IDebugBinder3:: gettyetargumentcount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3118d7e0fc4f493013a9a328cda0682fcc0707aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174003"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Diese Methode gibt die Anzahl von Argument Typen zurück, die diesem-Objekt zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>Parameter
`uCount`\
vorgenommen Anzahl von Argument Typen, die diesem-Objekt zugeordnet sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der von dieser Methode zurückgegebene Wert kann verwendet werden, um ein Array für die Verwendung mit der [gettypeer Arguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) -Methode zuzuordnen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)
