---
description: Diese Methode ruft den Arbeitsspeicher Kontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.
title: 'Idebugbinder:: Bind | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c373fbdae030de30544c67c1509eb812b746b7f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143657"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Diese Methode ruft den Arbeitsspeicher Kontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pContainer`\
in Das [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) , das das untergeordnete Element enthält, auf das verweist `pField` .

`pField`\
in Das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) , das das Symbol darstellt.

`ppObject`\
vorgenommen Gibt den zurück `IDebugObject` , der die Instanz des Symbols darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
