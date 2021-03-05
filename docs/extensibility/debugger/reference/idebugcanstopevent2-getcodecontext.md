---
description: Ruft den Code Kontext ab, der den Speicherort dieses Ereignisses beschreibt.
title: 'IDebugCanStopEvent2:: getcodecontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29863a16d59528e86f7c5a3449e7c321b2dcaf9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173536"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Ruft den Code Kontext ab, der den Speicherort dieses Ereignisses beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parameter
`ppCodeContext`\
vorgenommen Gibt das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt zurück, das den aktuellen Speicherort des Codes darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Bei den meisten Lauf Zeit Architekturen kann ein Code Kontext als eine Adresse im ausführungsstream eines Programms betrachtet werden, die auf eine bestimmte Anweisung zeigt.

 Um den Dokument Kontext abzurufen, der auf Zeilen des Quellcodes ausgerichtet ist, müssen Sie die [getdocumentcontext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
