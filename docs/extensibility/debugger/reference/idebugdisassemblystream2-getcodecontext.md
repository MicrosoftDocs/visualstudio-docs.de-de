---
title: 'IDebugDisassemblyStream2:: getcodecontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9bd0c78853a41c7efa7907fd1004277862721dc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928418"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Gibt ein Code Kontext Objekt zurück, das einem angegebenen Bezeichner für den Code Speicherort entspricht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parameter
`uCodeLocationId`\
in Gibt den Bezeichner des Code Speicher Orts an. Eine Beschreibung eines Code Speicherort Bezeichners finden Sie im Abschnitt "Hinweise" der Methode " [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) ".

`ppCodeContext`\
vorgenommen Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt zurück, das den zugeordneten Code Kontext darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Bezeichner für den Code Speicherort kann von einem Rückruf der [getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) -Methode zurückgegeben werden und kann in der [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur vorkommen.

 Um einen Code Kontext in einen Bezeichner für den Code Speicherort zu konvertieren, müssen Sie die [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
