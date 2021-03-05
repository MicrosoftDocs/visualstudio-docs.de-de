---
description: Ruft den übergeordneten Verweis eines Verweises ab.
title: 'IDebugReference2:: GetParent | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eee5015a304b3f4939c06664606a7d4aa8803f02
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165981"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Ruft den übergeordneten Verweis eines Verweises ab. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

## <a name="parameters"></a>Parameter
`ppParent`\
vorgenommen Gibt ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt zurück, das das übergeordnete Element dieser Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
