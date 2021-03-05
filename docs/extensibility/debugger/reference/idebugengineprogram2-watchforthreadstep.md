---
description: Überwacht, dass die Ausführung im angegebenen Thread erfolgt (oder die Überwachung auf die Ausführung anhält).
title: 'IDebugEngineProgram2:: watchan Step | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf02e07bebbbfd711d99ef7605befbdce1f9376
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153416"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Überwacht, dass die Ausführung im angegebenen Thread erfolgt (oder die Überwachung auf die Ausführung anhält).

## <a name="syntax"></a>Syntax

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parameter
`pOriginatingProgram`\
in Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das abgestufte Programm darstellt.

`dwTid`\
in Gibt den Bezeichner des zu überwachenden Threads an.

`fWatch`\
in Ungleich 0 (NULL `TRUE` ) bedeutet, dass die Ausführung auf dem durch identifizierten Thread überwacht `dwTid` werden soll; andernfalls `FALSE` bedeutet NULL (), dass die Ausführung für nicht mehr überwacht werden kann `dwTid` .

`dwFrame`\
in Gibt einen Frame Index an, der den Schritttyp steuert. Wenn dieser Wert 0 (null) ist, ist der Schritttyp "Einzelschritt", und das Programm sollte angehalten werden, wenn der von identifizierte Thread `dwTid` ausgeführt wird. Wenn ungleich `dwFrame` 0 (null) ist, ist der Schritttyp "Step over", und das Programm sollte nur beendet werden, wenn der von identifizierte Thread `dwTid` in einem Frame ausgeführt wird, dessen Index im Stapel gleich oder höher ist `dwFrame` .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn der Sitzungs-Debug-Manager (SDM) ein Programm durchführt, das durch den- `pOriginatingProgram` Parameter identifiziert wird, werden alle anderen angefügten Programme durch Aufrufen dieser Methode benachrichtigt.

 Diese Methode gilt nur für den Schritt des gleichen Threads.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
