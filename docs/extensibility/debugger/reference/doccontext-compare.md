---
title: DOCCONTEXT_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db66748a1665d5ab965f20295258efd65ec43d38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953720"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Gibt die Kriterien für den Vergleich von zwei Dokument Kontexten an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Felder
`DOCCONTEXT_EQUAL`\
Suchen Sie den ersten Dokument Kontext in der Liste, der dem Zieldokument Kontext entspricht.

`DOCCONTEXT_LESS_THAN`\
Suchen Sie den ersten Dokument Kontext in der Liste, der kleiner ist als der Zieldokument Kontext.

`DOCCONTEXT_GREATER_THAN`\
Suchen Sie den ersten Dokument Kontext in der Liste, der größer ist als der Zieldokument Kontext.

`DOCCONTEXT_SAME_DOCUMENT`\
Suchen Sie den ersten Dokument Kontext in der Liste, der sich im selben Dokument wie der Zieldokument Kontext befindet.

## <a name="remarks"></a>Bemerkungen
Als Argument an die [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) -Methode übergebenen.

Diese Werte werden verwendet, um ein Vergleichskriterium für die Suche nach dem ersten Dokument Kontext in einer Liste anzugeben. Einem Dokument Kontext wird eine Liste mit Dokument Kontexten zugewiesen, mit denen er sich über die-Methode vergleichen kann `IDebugDocumentContext2::Compare` . Der erste Dokument Kontext in der Liste, für den der Vergleichs Operator ist, `true` wird zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
