---
description: Fügt eine Debug-Engine (de) an ein Programm oder eine Programmdatei an.
title: 'IDebugEngine2:: Attach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a780ab04e693fd2868579efbf015aef25e0cca32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160147"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Fügt eine Debug-Engine (de) an ein Programm oder eine Programmdatei an. Wird vom Sitzungs-Debug-Manager (SDM) aufgerufen, wenn der Prozess Prozess interne Ausführung in SDM erfolgt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parameter
`pProgram`\
in Ein Array von [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekten, die Programme darstellen, an die angefügt werden soll. Dabei handelt es sich um Port Programme.

`rgpProgramNodes`\
in Ein Array von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekten, die Programmknoten darstellen, eine für jedes Programm. Die Programmknoten in diesem Array stellen dieselben Programme wie in dar `pProgram` . Die Programmknoten werden angegeben, damit der de die Programme identifizieren kann, an die das Anfügen angefügt werden soll.

`celtPrograms`\
in Anzahl der Programme und/oder Programmknoten in den `pProgram` -und- `rgpProgramNodes` Arrays.

`pCallback`\
in Das [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das zum Senden von debuggingereignissen an SDM verwendet werden soll.

`dwReason`\
in Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) Enumeration, die den Grund für das Anfügen dieser Programme angibt. Weitere Informationen finden Sie im Abschnitt "Hinweise".

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es gibt drei Gründe für das Anfügen an ein Programm, wie im folgenden dargestellt:

- `ATTACH_REASON_LAUNCH` Gibt an, dass die de an das Programm angefügt wird, da der Benutzer den Prozess gestartet hat, der ihn enthält.

- `ATTACH_REASON_USER` Gibt an, dass der Benutzer explizit das Anfügen an ein Programm (oder den Prozess mit einem Programm) angefordert hat.

- `ATTACH_REASON_AUTO` Gibt an, dass die de an ein bestimmtes Programm angefügt wird, da Sie bereits andere Programme in einem bestimmten Prozess debuggt. Dies wird auch als automatische Anfügung bezeichnet.

  Wenn diese Methode aufgerufen wird, muss der de diese Ereignisse nacheinander senden:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (wenn Sie nicht bereits für eine bestimmte Instanz der Debug-Engine gesendet wurde)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Wenn der Grund für das Anfügen ist `ATTACH_REASON_LAUNCH` , muss das Ereignis "de" das [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) -Ereignis senden.

   Wenn das Objekt "de" das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt abruft, das dem gedepufferten Programm entspricht, kann es für jede beliebige private Schnittstelle abgefragt werden.

   Vor dem Aufrufen der Methoden eines Programm Knotens im Array, das von oder angegeben wird, sollte der Identitätswechsel bei `pProgram` `rgpProgramNodes` Bedarf für die Schnittstelle aktiviert werden, die `IDebugProgram2` den Programmknoten darstellt. Normalerweise ist dieser Schritt jedoch nicht erforderlich. Weitere Informationen finden Sie unter [Sicherheitsprobleme](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
