---
description: Macht ein Programm zum dedebugging verfügbar.
title: 'IDebugProgramPublisher2:: unpublishprogram | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7160b3bd3b954b722828542e8eead4fc6fedebf5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161260"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Macht ein Programm zum dedebugging verfügbar.

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parameter
`pDebuggeeInterface`\
in Eine `IUnknown` Schnittstelle zum Programm. Dies ist der gleiche Wert, der für die [publishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) -Methode bereitgestellt wird, und das Programm, das entfernt wird, eindeutig identifiziert (d. h., es wird als Cookie verwendet).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie die [publishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) -Methode, um ein Programm für die Debug-engines und den Sitzungs-Debug-Manager verfügbar zu machen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
