---
description: Ruft die Arbeitsspeicher Bytes ab, die den Wert einer Eigenschaft bilden.
title: 'IDebugProperty2:: getmemorybytes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcfb88c167c47a5802edfc2a4dc1b3f765659a1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166917"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
Ruft die Arbeitsspeicher Bytes ab, die den Wert einer Eigenschaft bilden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parameter
`ppMemoryBytes`\
vorgenommen Gibt ein [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt zurück, das verwendet werden kann, um den Arbeitsspeicher abzurufen, der den Wert der-Eigenschaft enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Gibt zurück `S_GETMEMORYBYTES_NO_MEMORY_BYTES` , wenn keine Speicher Bytes abgerufen werden müssen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
