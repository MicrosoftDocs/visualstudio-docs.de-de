---
title: 'Idebugarrayobject:: GetDimensions | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c0c71032fc8f5c75522f6b1f9e0d8cb1308f63f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870193"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ruft die Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
in Die Anzahl der abzurufenden Dimensionen.

`dwDimensions`\
[in, out] Ein Array, das mit den Größen der einzelnen Dimensionen aufgefüllt wird. `dwCount` Gibt die maximale Größe des `dwDimensions` Arrays an.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein mehrdimensionales Array kann für jede Dimension über unterschiedliche Größen verfügen. Bei Angabe des dreidimensionalen Arrays `myarray[3][2][6]` würde diese Methode z. b. 3, 2 und 6 im- `dwDimensions` Parameter in dieser Reihenfolge zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
