---
description: Bestimmt, ob der aktuelle Anweisungs Zeiger auf den angegebenen Stapel Rahmen festgelegt werden kann.
title: 'IDebugThread2:: cansetnextstatement | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b07eb23127abedc4e41af2795c3452401c3e670
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168386"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Bestimmt, ob der aktuelle Anweisungs Zeiger auf den angegebenen Stapel Rahmen festgelegt werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parameter
`pStackFrame`\
Für zukünftige Verwendung reserviert. Legen Sie auf einen NULL-Wert fest. Wenn dies ein NULL-Wert ist, verwenden Sie den aktuellen Stapel Rahmen.

`pCodeContext`\
in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den Code Speicherort beschreibt, der ausgeführt werden soll, und seinen Kontext.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn diese Methode zurückgibt `S_OK` , wird die [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) -Methode aufgerufen, um die nächste Anweisung tatsächlich festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
