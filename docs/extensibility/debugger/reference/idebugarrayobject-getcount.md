---
description: Ruft die Anzahl der Elemente im Array ab.
title: 'Idebugarrayobject:: GetCount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dafff955eb0801ffe13f76f61d8f7451398e41e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158695"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Ruft die Anzahl der Elemente im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parameter
`pdwElements`\
vorgenommen Gibt die Anzahl zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode sieht alle Elemente eines Array Objekts als eindimensionales Array, auch wenn das Array Objekt mehrdimensional ist. Bei Angabe des Arrays `myarray[3][2][6]` würde diese Methode z. b. 36 im- `pdwElements` Parameter zurückgeben. Verwenden Sie die [getElements](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) -Methode, um die einzelnen Elemente nacheinander abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
