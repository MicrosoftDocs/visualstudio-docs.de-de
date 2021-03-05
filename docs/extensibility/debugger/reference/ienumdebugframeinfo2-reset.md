---
description: Setzt die Enumeration auf das erste frameInfo-Element zurück.
title: 'IEnumDebugFrameInfo2:: Reset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Reset
helpviewer_keywords:
- IEnumDebugFrameInfo2::Reset
ms.assetid: e149b559-f072-480b-9552-a452b147f3a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01a7a2be3986798e087e4bc4096be2b8ce1454ad
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226435"
---
# <a name="ienumdebugframeinfo2reset"></a>IEnumDebugFrameInfo2::Reset
Setzt die Enumeration auf das erste Element zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) -Methode das erste Element der-Enumeration zurück.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
