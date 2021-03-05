---
description: Ruft den Dokument Kontext ab, der diesem Code Kontext entspricht.
title: 'IDebugCodeContext2:: getdocumentcontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b67e76c8cc8719c77c88c8b93ca667c3a025a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164161"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ruft den Dokument Kontext ab, der diesem Code Kontext entspricht. Der Dokument Kontext stellt eine Position in der Quelldatei dar, die dem Quellcode entspricht, der diese Anweisung generiert hat.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parameter
`ppSrcCxt`\
vorgenommen Gibt das [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Objekt zurück, das dem Code Kontext entspricht. Wenn `S_OK` zurückgegeben wird, sollten THS nicht-sein `null` .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Eine Debug-Engine sollte einen Fehlercode zurückgeben, z `E_FAIL` . b. wenn der- `out` Parameter ist, wenn `null` der Code Kontext keine Quell Position aufweist.

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen kann der Dokument Kontext als Position in einer Quelldatei betrachtet werden, während der Code Kontext eine Position einer Code Anweisung in einem ausführungsstream ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
