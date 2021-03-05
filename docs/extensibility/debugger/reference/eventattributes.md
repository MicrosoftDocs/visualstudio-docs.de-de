---
description: Gibt die Ereignis Attribute an.
title: Eventattribute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6b56e815d8145e3f870468751a0978475245c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150886"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Gibt die Ereignis Attribute an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Felder
`EVENT_ASYNCHRONOUS`\
Gibt an, dass das Ereignis asynchron ist und keine Antwort auf das Ereignis benötigt wird.

`EVENT_SYNCHRONOUS`\
Gibt an, dass das Ereignis synchron ist. Antworten mithilfe von [continuefromsynchronoutsvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Gibt an, dass dies ein anhalteereignis ist. Muss mit oder kombiniert werden `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Gibt ein asynchrones anhalteereignis an. Zurzeit ist kein derartiges Ereignis vorhanden. Dieses Flag ist nur ein Platzhalter.

`EVENT_SYNC_STOP`\
Gibt ein synchrones anhalteereignis an (eine Kombination aus `EVENT_SYNCHRONOUS` und `EVENT_STOPPING` ). Dieser Wert wird von einer Debug-Engine (de) verwendet, wenn ein anhalteereignis gesendet wird. Die Antwort wird durch einen aufzurufenden [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)-, [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)-oder [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)-Befehl gemacht.

`EVENT_IMMEDIATE`\
Gibt ein Ereignis an, das sofort und synchron an die IDE gesendet wird. Dieses Flag wird mit anderen Flags wie `EVENT_ASYNCHRONOUS` , oder kombiniert, `EVENT_SYNCHRONOUS` `EVENT_SYNC_STOP` um den Ereignistyp anzugeben, und die Tatsache, dass der Antwortmechanismus (sofern vorhanden) bekannt ist.

`EVENT_EXPRESSION_EVALUATION`\
Das Ereignis ist das Ergebnis der Ausdrucks Auswertung.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden im- `dwAttrib` Parameter der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode übergeben.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
