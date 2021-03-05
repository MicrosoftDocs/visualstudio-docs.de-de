---
description: Ruft den Quell Code Bereich dieses Dokument Kontexts ab.
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d02dfbd93002bedadd4c82168d498f89050ddc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162900"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ruft den Quell Code Bereich dieses Dokument Kontexts ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
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
 Ein Quellbereich ist der gesamte Bereich des Quellcodes, von der aktuellen Anweisung bis zum direkt nach der vorhergehenden Anweisung, die Code bereitgestellt hat. Der Quellbereich wird in der Regel zum Mischen von Quell Anweisungen, einschließlich Kommentaren, mit Code im Fenster Disassembly verwendet.

 Um den Bereich nur für die Code Anweisungen zu erhalten, die in diesem Dokument Kontext enthalten sind, müssen Sie die [getstatuementrange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
