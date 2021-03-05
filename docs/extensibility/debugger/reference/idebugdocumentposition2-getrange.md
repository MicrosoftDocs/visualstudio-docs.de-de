---
description: Ruft den Bereich für diese Dokument Position ab.
title: 'IDebugDocumentPosition2:: GetRange | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e886891c0d971bdad0916d5b243993e46a7ba57
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162718"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Ruft den Bereich für diese Dokument Position ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parameter
`pBegPosition`\
[in, out] Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit der Anfangs Position ausgefüllt ist. Legen Sie dieses Argument auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

`pEndPosition`\
[in, out] Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit der Endposition ausgefüllt ist. Legen Sie dieses Argument auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der in einer Dokument Position für einen Location-Breakpoint angegebene Bereich wird von der Debug-Engine (de) verwendet, um nach einer Anweisung zu suchen, die tatsächlich Code beiträgt. Beachten Sie z. B. folgenden Code:

```
Line 5: // comment
Line 6: x = 1;
```

 Zeile 5 trägt keinen Code zu dem Programm bei, das gedeppt wird. Wenn der Debugger, der den Breakpoint in Zeile 5 festlegt, eine bestimmte Menge für die erste Zeile, die Code beiträgt, durchsucht, würde der Debugger einen Bereich angeben, der zusätzliche Kandidaten Zeilen enthält, in denen ein Haltepunkt ordnungsgemäß platziert werden kann. Der de würde dann diese Zeilen durchsuchen, bis eine Zeile gefunden wird, die einen Haltepunkt akzeptieren könnte.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
