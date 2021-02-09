---
title: 'IDebugDocumentContext2:: Compare | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 959d909d0c777110905aff3b11c8c29d27d628dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880761"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Vergleicht diesen Dokument Kontext mit einem angegebenen Array von Dokument Kontexten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parameter
`compare`\
in Ein Wert aus der [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) Enumeration, der den Typ des Vergleichs angibt.

`rgpDocContextSet`\
in Ein Array von [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Objekten, die die Dokument Kontexte darstellen, die mit verglichen werden.

`dwDocContextSetLen`\
in Die Länge des zu vergleichenden Array von Dokument Kontexten.

`pdwDocContext`\
vorgenommen Gibt den Index in das `rgpDocContextSet` Array des ersten Dokument Kontexts zurück, der den Vergleich erfüllt.

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, `S_OK` Wenn eine Entsprechung gefunden wurde. Gibt zurück, `S_FALSE` Wenn keine Entsprechung gefunden wurde. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Objekte, die im Array weitergegeben werden, müssen von derselben Debug-Engine implementiert werden, die das Objekt implementiert, das `IDebugDocumentContext2` aufgerufen wird. andernfalls ist der Vergleich nicht gültig.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
