---
description: Verschiebt den Dokument Kontext um eine angegebene Anzahl von Anweisungen oder Zeilen.
title: 'IDebugDocumentContext2:: Seek | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a70b8fac8e084a78b1a29ae941f1d03d6552f860
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162848"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Verschiebt den Dokument Kontext um eine angegebene Anzahl von Anweisungen oder Zeilen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parameter
`nCount`\
in Die Anzahl der Anweisungen oder Zeilen, die je nach Dokument Kontext vorwärts verschoben werden.

`ppDocContext`\
vorgenommen Gibt ein neues [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Objekt mit der neuen Position zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
