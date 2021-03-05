---
description: Legt den Wert eines Verweises aus einem anderen Verweis fest.
title: 'IDebugReference2:: setvalueasreference | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84117f4a9eb925b442be86a73736479a05818ca1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165942"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Legt den Wert eines Verweises aus einem anderen Verweis fest. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parameter
`rgpArgs`\
in Ein Array von [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekten, mit denen bestimmt wird, wie der Verweis Wert festgelegt wird.

`dwArgCount`\
in Die Anzahl der Verweise im Array.

`pValue`\
in Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt, aus dem der Eigenschafts Wert festgelegt wird.

`dwTimeout`\
in Maximale Zeit in Millisekunden, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
