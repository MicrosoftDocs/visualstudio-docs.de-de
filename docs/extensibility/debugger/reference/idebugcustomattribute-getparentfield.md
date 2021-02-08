---
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
ms.openlocfilehash: b9845954a2be9ec57edb6ca555fb89a6ad20f7d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842471"
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
