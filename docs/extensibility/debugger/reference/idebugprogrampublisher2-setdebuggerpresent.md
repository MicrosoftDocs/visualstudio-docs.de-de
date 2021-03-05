---
description: Weist den Programm Verleger an, dass ein Debugger vorhanden ist und ausgeführt wird.
title: 'IDebugProgramPublisher2:: setdebug-vorhanden | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3db8703ed05fd4a386b9265998de2f27017d0d76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161286"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Weist den Programm Verleger an, dass ein Debugger vorhanden ist und ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Parameter
`fDebuggerPresent`\
in Ungleich NULL ( `TRUE` ), wenn ein Debugger vorhanden ist, andernfalls 0 (NULL `FALSE` ) (), wenn dies nicht der Fall ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das vorhanden sein oder Fehlen eines Debuggers wird in den Daten widergespiegelt, die von der [getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) -Methode zurückgegeben werden: der zurückgegebene Wert wird durch einen vorherigen-Aufrufsatz der-Methode festgelegt oder gelöscht `SetDebuggerPresent` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
