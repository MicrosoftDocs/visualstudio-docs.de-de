---
description: Diese Methode ruft ein Speicher Objekt ab, das den Speicher darstellt, an den dieses Objekt gebunden ist.
title: 'IDebugBinder3:: getmemoryobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ca708c9a6fd80a7a04d8202a73f0bce99102ff1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173973"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Diese Methode ruft ein Speicher Objekt ab, das den Speicher darstellt, an den dieses Objekt gebunden ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pField`\
in Gibt an, für welches Feld das Speicher Objekt zu erhalten ist.

`uConstant`\
in Stellt eine Speicheradresse oder einen Wert für einen konstanten Wert dar.

`ppObject`\
vorgenommen Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das den Speicher darstellt, an den dieses Objekt gebunden ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
