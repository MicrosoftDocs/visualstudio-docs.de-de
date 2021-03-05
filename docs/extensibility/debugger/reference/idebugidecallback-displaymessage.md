---
description: Sendet die angegebene Meldungs Zeichenfolge an das Ausgabefenster des Debuggers.
title: Idebugidebug::D isplaymess | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab7223d065df0bb77c2782ef7f66d14843a23f62
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172544"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Sendet die angegebene Meldungs Zeichenfolge an das Ausgabefenster des Debuggers.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisplayMessage (
   LPCOLESTR szMessage
);
```

```csharp
int DisplayMessage (
   string szMessage
);
```

## <a name="parameters"></a>Parameter
`szMessage`\
in Meldungs Zeichenfolge, die im Ausgabefenster des Debuggers angezeigt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
