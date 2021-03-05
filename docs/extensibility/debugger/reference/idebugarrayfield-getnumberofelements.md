---
description: Ruft die Anzahl der Elemente im Array ab.
title: 'Idebugarrayfield:: getnummeriofelements | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 237cc74b2a34c78104e001bcc5a3b13dd6c7bd43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143830"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Ruft die Anzahl der Elemente im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parameter
`pdwNumElements`\
vorgenommen Gibt die Anzahl der Elemente im Array zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der zurückgegebene Wert ist die Gesamtzahl der Elemente im Array, unabhängig von der Anzahl von Dimensionen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
