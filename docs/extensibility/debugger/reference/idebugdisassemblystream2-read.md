---
title: 'IDebugDisassemblyStream2:: Read | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732095"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Liest Anweisungen ab der aktuellen Position im disassemblystream.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parameter
`dwInstructions`\
in Die Anzahl der Anweisungen für die Disassemblierung. Dieser Wert ist auch die maximale Länge des `prgDisassembly` Arrays.

`dwFields`\
in Eine Kombination von Flags aus der [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Enumeration, die angeben, welche Felder von `prgDisassembly` ausgefüllt werden sollen.

`pdwInstructionsRead`\
vorgenommen Gibt die Anzahl der tatsächlich disassemblierten Anweisungen zurück.

`prgDisassembly`\
vorgenommen Ein Array von [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Strukturen, das mit dem disassemblierten Code gefüllt ist, eine Struktur pro disassemblierten Anweisung. Die Länge dieses Arrays wird durch den- `dwInstructions` Parameter vorgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die maximale Anzahl von Anweisungen, die im aktuellen Gültigkeitsbereich verfügbar sind, kann durch Aufrufen der [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) -Methode abgerufen werden.

 Die aktuelle Position, von der aus die nächste Anweisung gelesen wird, kann durch Aufrufen der [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) -Methode geändert werden.

 Das- `DSF_OPERANDS_SYMBOLS` Flag kann dem-Flag im-Parameter hinzugefügt werden `DSF_OPERANDS` `dwFields` , um anzugeben, dass bei der disassemblierungsanweisung Symbolnamen verwendet werden sollen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
