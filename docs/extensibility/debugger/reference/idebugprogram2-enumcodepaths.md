---
description: Ruft eine Liste der Codepfade für eine angegebene Position in einer Quelldatei ab.
title: 'IDebugProgram2:: enumcodepath | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c647379d0b72832a4068d720846f8a9331f9b939
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159964"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Ruft eine Liste der Codepfade für eine angegebene Position in einer Quelldatei ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parameter
`pszHint`\
in Das Wort unter dem Cursor in der **Quell** -oder disassemblyansicht in der IDE. 

`pStart`\
in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den aktuellen Code Kontext darstellt.

`pFrame`\
in Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Objekt, das den dem aktuellen Haltepunkt zugeordneten Stapel Rahmen darstellt.

`fSource`\
in Ungleich NULL ( `TRUE` ), wenn in der **Quell** Ansicht, oder 0 (NULL `FALSE` ) (), wenn in der disassemblyansicht. 

`ppEnum`\
vorgenommen Gibt ein [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) -Objekt zurück, das eine Liste der Codepfade enthält.

`ppSafety`\
vorgenommen Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt zurück, das einen zusätzlichen Code Kontext darstellt, der als Haltepunkt festgelegt werden soll, wenn der ausgewählte Codepfad übersprungen wird. Dies kann bei einem booleschen Ausdruck mit kurzer Umschaltung vorkommen, z. b..

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Codepfad beschreibt den Namen einer Methode oder Funktion, die aufgerufen wurde, um zum aktuellen Punkt während der Ausführung des Programms zu gelangen. Eine Liste von Codepfade stellt die-Aufrufliste dar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
