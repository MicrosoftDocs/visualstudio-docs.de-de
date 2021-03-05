---
description: Ruft das enthaltende Dokument ab.
title: 'IDebugDocumentPosition2:: GetDocument | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetDocument
helpviewer_keywords:
- IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0153b55397b78191d1e2ddc022767095bc1fcd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162796"
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
Ruft das enthaltende Dokument ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Parameter
`ppDoc`\
vorgenommen Gibt ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Objekt zurück, das das Dokument darstellt, das diese Position enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
