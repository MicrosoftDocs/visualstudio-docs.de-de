---
description: Erstellt ein Zeichen folgen Objekt.
title: 'Idebugfunctionobject:: kreatestringobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78d9d0be09ee8fa6374273ad308616a7d294c8cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166475"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Erstellt ein Zeichen folgen Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Parameter
`pcstrString`\
in Der Zeichen folgen Wert für das Zeichen folgen Objekt.

`ppObject`\
vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das neu erstellte Zeichen folgen Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Zeichenfolge darstellt, die ein Parameter für die Funktion ist, die durch die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle dargestellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
