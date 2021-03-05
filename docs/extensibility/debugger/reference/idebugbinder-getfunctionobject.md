---
description: Diese Methode ruft ein idebugfunctionobject-Objekt ab, das verwendet wird, um Funktionsparameter zu erstellen.
title: 'Idebugbinder:: getfunctionobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9868edafb18a129d119a818d9e51363d4964afa2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143649"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Diese Methode ruft ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt ab, das verwendet wird, um Funktionsparameter zu erstellen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parameter
`ppFunction`\
vorgenommen Gibt die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle zurück, die verwendet wird, um Funktionsparameter zu erstellen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
