---
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
ms.openlocfilehash: 17a3623ab0a674b49d96d6eb77f04ec0de9a2fb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842252"
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
