---
title: 'IDebugMemoryContext2:: Subtract | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71e3191384a0ee45778cb7ee37b7e55e5f673578
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851087"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Subtrahiert den angegebenen Wert aus dem aktuellen Kontext und gibt einen neuen Kontext zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
in Die Anzahl der zu dekreterenden Speicher Bytes.

`ppMemCxt`\
vorgenommen Gibt ein neues [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Speicher Kontext ist eine Adresse, sodass das Subtrahieren eines Werts von einer Adresse eine neue Adresse erzeugt, die eine neue Kontext Schnittstelle erfordert.

 Diese Methode muss immer einen neuen Kontext ergeben, auch wenn sich die resultierende Adresse außerhalb des Speicherplatzes befindet, der diesem Kontext zugeordnet ist. Die einzige Ausnahme ist, wenn kein Arbeitsspeicher für den neuen Kontext zugeordnet werden kann oder wenn `ppMemCxt` ein NULL-Wert ist (bei dem es sich um einen Fehler handelt).

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
