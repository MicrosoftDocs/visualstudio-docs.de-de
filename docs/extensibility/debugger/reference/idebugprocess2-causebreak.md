---
description: Fordert an, dass das nächste Programm, das Code in diesem Prozess ausgeführt, ein IDebugBreakEvent2-Ereignis Objekt stoppt und sendet.
title: 'IDebugProcess2:: causeelbreak | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28a4da4c0f7e4f8770478a47a73f7567506d5ae2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161397"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Fordert an, dass das nächste Programm, das Code in diesem Prozess ausgeführt, ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Ereignis Objekt stoppt und sendet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
