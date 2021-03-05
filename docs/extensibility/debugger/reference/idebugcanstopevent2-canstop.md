---
description: Benachrichtigt die Debug-Engine (de), ob Sie am aktuellen Code Speicherort anhalten oder die Ausführung einfach fortsetzen möchten.
title: 'IDebugCanStopEvent2:: canstoppt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38b4d528ae1aa5a89853dc4873a9c07aa051a14c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173635"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Benachrichtigt die Debug-Engine (de), ob Sie am aktuellen Code Speicherort anhalten oder die Ausführung einfach fortsetzen möchten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parameter
`fCanStop`\
in Ungleich NULL ( `TRUE` ), wenn die de an der aktuellen Codeposition angehalten werden soll, andernfalls 0 (NULL `FALSE` ) ().

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Empfänger dieses Ereignisses ruft in der Regel die [geverrat](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) -Methode auf, um die Ursache zu bestimmen, warum die Anforderung beendet werden soll, und ruft dann die- `IDebugCanStopEvent2::CanStop` Methode mit der entsprechenden Antwort auf.

 Wenn der Dienst beendet wird, sendet er ein Ereignis, das den Grund für den Stopp beschreibt. Es gibt in der Regel zwei Ereignisse, die gesendet werden, einen Benutzer-oder Signal Umbruch, der durch die [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Schnittstelle dargestellt wird, und ein Haltepunkt Ereignis, das von der [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnitt

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
