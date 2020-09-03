---
title: 'IDebugProgramEngines2:: enumpossibleengines | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722435"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Gibt die GUIDs für alle möglichen debugengines (de) zurück, die das Programm debuggen können.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parameter
`celtBuffer`\
in Die Anzahl der zurück zugebende de-GUIDs. Dies gibt auch die maximale Größe des `rgguidEngines` Arrays an.

`rgguidEngines`\
[in, out] Ein Array von de GUIDs, das ausgefüllt werden soll.

`pceltEngines`\
vorgenommen Gibt die tatsächliche Anzahl von de GUIDs zurück, die zurückgegeben werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` oder [c#] 0x8007007a zurück, wenn der Puffer nicht groß genug ist.

## <a name="remarks"></a>Bemerkungen
 Um zu ermitteln, wie viele Engines vorhanden sind, müssen Sie diese Methode einmal aufrufen, wobei der `celtBuffer` -Parameter auf 0 festgelegt ist und der- `rgguidEngines` Parameter auf einen NULL-Wert festgelegt ist. Dies gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007a für c#) zurück, und der- `pceltEngines` Parameter gibt die erforderliche Größe des Puffers zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
