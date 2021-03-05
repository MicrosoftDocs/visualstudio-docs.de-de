---
description: Bestimmt, ob die Dokument Position im angegebenen Dokument enthalten ist.
title: 'IDebugDocumentPosition2:: ispositionindocument | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4800f3735e2d015e3638a642e8c0d54829ddd4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154287"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Bestimmt, ob die Dokument Position im angegebenen Dokument enthalten ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Parameter
`pDoc`\
in Das [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Objekt, das den enthaltenden Dokument Kandidaten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird hauptsächlich beim Festlegen von Breakpoints in [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstellen verwendet. Beim Laden von Dokumenten wird die Haltepunkt Position aufgerufen, um zu bestimmen, ob das Dokument diese Position enthält.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
