---
description: Ruft die Größe des Werts des Verweises in Bytes ab.
title: 'IDebugReference2:: GetSize | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e653a88adcf6388ab31d7ba5ae2cf526c5c84bae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165968"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Ruft die Größe des Werts des Verweises in Bytes ab. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parameter
`pdwSize`\
vorgenommen Gibt die Größe des Verweises in Byte zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
