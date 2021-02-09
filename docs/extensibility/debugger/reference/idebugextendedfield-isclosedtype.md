---
title: 'Idebugextendedfield:: isclosedtype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 404b1852e0db27673ea62569b25013a7f999f16d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915496"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Bestimmt, ob das Feld einen geschlossenen Typ darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Rückgabewert
 Wenn das Feld ein geschlossener Typ ist, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
