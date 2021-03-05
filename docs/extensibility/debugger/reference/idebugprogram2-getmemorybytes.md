---
description: Ruft die vom Programm belegten Arbeitsspeicher Bytes ab.
title: 'IDebugProgram2:: getmemorybytes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e63d25807e6a434066c7fc3bb860e9657faadf15
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165994"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Ruft die vom Programm belegten Arbeitsspeicher Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryBytes( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parameter
`ppMemoryBytes`\
vorgenommen Gibt ein [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt zurück, das die Arbeitsspeicher Bytes des Programms darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die vom [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt dargestellten Arbeitsspeicher Bytes richten sich nach dem Bild des Programms im Arbeitsspeicher und nicht nach dem Arbeitsspeicher, der beim Ausführen des Programms zugewiesen wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
