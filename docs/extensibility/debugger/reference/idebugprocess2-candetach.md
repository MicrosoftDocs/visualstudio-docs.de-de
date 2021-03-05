---
description: Bestimmt, ob der Sitzungs-Debug-Manager (SDM) den Prozess trennen kann.
title: 'IDebugProcess2:: candetach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e876d5642cf8a4b7b60f5119839e64959f296e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151674"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Bestimmt, ob der Sitzungs-Debug-Manager (SDM) den Prozess trennen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben, `S_OK.` `S_FALSE` Wenn der Debugger nicht vom Prozess trennen kann. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
