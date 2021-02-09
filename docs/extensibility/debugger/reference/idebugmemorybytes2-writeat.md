---
title: 'IDebugMemoryBytes2:: Write-at | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ff77985bca8772d92c3b90e7a727c0077137e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909903"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Schreibt die angegebene Anzahl von Bytes an Arbeitsspeicher, beginnend bei der angegebenen Adresse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parameter
`pStartContext`\
in Das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt, das angibt, wohin das Schreiben von Bytes beginnen soll.

`dwCount`\
[in] Die Anzahl der zu schreibenden Bytes.

`rgbMemory`\
in Die zu schreibende bytes. Es wird davon ausgegangen, dass die Größe dieses Arrays mindestens `dwCount` Byte groß ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` Wenn nicht alle Bytes geschrieben werden könnten oder ein Fehlercode zurückgegeben wird (in der Regel `E_FAIL` ).

## <a name="remarks"></a>Bemerkungen
 Wenn sich die Anfangsadresse nicht im Arbeitsspeicher Fenster befindet, das durch dieses [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt dargestellt wird, wird kein Schreibvorgang ausgeführt, und es wird ein Fehlercode von `E_FAIL` zurückgegeben – auch wenn sich der zu schreibende Betrag im Speicherbereich überlappt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
