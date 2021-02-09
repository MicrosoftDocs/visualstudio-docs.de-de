---
title: 'IDebugReference2:: Compare | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cebc34bdd1515ad632a0165fcdc900999b383fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909737"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Vergleicht einen Verweis auf einen anderen. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parameter
`dwCompare`\
in Ein Wert aus der [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) Enumeration, der den Vergleichs Vorgang angibt, z. b. gleich, kleiner als oder größer als.

`pReference`\
in Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt, das den Verweis darstellt, mit dem verglichen werden soll.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
