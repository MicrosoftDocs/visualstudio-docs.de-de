---
description: Fügt dem aktuellen Kontext den angegebenen Wert hinzu und gibt einen neuen Kontext zurück.
title: 'IDebugMemoryContext2:: Add | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59daddd38daff2f04f12bc0d1be4e06ec90cf723
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166423"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Fügt dem aktuellen Kontext den angegebenen Wert hinzu und gibt einen neuen Kontext zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
in Der Wert, der dem aktuellen Kontext hinzugefügt werden soll.

`ppMemCxt`\
vorgenommen Gibt ein neues [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Speicher Kontext ist eine Adresse. das Hinzufügen eines Werts zu einer Adresse erzeugt also eine neue Adresse, die eine neue Kontext Schnittstelle erfordert.

 Diese Methode muss immer einen neuen Kontext ergeben, auch wenn sich die resultierende Adresse außerhalb des Speicherplatzes befindet, der diesem Kontext zugeordnet ist. Die einzige Ausnahme ist, wenn kein Arbeitsspeicher für den neuen Kontext zugeordnet werden kann oder wenn `ppMemCxt` ein NULL-Wert ist (bei dem es sich um einen Fehler handelt).

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
