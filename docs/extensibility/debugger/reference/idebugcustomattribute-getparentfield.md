---
description: Ruft das Feld ab, an das das benutzerdefinierte Attribut angefügt wird.
title: 'Idebugcustomattribute:: gettientfield | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4af4569b64a41fc84a09c7e8f2ce0a8f6b42e86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154508"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Ruft das Feld ab, an das das benutzerdefinierte Attribut angefügt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt zurück, das das Feld darstellt, an das das benutzerdefinierte Attribut angefügt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Aufrufen der [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für das zurückgegebene [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, um zu bestimmen, welche Art von Feld das übergeordnete Element ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
