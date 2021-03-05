---
description: Ruft den Speicher Kontext des Eigenschafts Werts ab.
title: 'IDebugProperty2:: getmemorycontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a82b2f0ed4a1fb7a37ec621d737d624d30d33ef2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166852"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Ruft den Speicher Kontext des Eigenschafts Werts ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Parameter
`ppMemory`\
vorgenommen Gibt das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt zurück, das den dieser Eigenschaft zugeordneten Arbeitsspeicher darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Gibt zurück `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` , wenn kein Speicher Kontext zum Abrufen vorhanden ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
