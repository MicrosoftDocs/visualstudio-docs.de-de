---
description: Ruft den Rang des Arrays ab, d. h. die Anzahl der Dimensionen.
title: 'Idebugarrayobject:: GetRank | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158539"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Ruft den Rang des Arrays ab, d. h. die Anzahl der Dimensionen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parameter
`pdwRank`\
vorgenommen Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie die [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) -Methode, um die Größe der einzelnen Dimensionen des Array-Objekts abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
