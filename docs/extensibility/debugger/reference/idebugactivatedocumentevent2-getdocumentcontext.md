---
title: 'IDebugActivateDocumentEvent2:: getdocumentcontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32bc4715438c7197628b4df66203aadb753bec25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904680"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Ruft den Dokument Kontext ab, der die Position im Dokument beschreibt, die vom Debugpaket aktiviert werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parameter
`ppDocContext`\
vorgenommen Gibt ein [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Objekt zurück, das eine Position in einem Quelldatei Dokument darstellt.

## <a name="remarks"></a>Bemerkungen
 Diese Position kann z. b. zum Anzeigen der Einfügemarke verwendet werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
