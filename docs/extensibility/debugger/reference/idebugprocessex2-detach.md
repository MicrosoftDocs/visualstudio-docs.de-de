---
title: IDebugProcessEx2::D Etach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62ca404442d6bf6080972f03c3e2fd0da2621e20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954890"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Diese Methode informiert den Prozess darüber, dass eine Sitzung den Prozess nicht mehr debuggt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parameter
`pSession`\
in Ein Wert, der die Sitzung eindeutig identifiziert, von der dieser Prozess getrennt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die übergebene Schnittstelle `pSession` muss nur als Cookie behandelt werden. dabei handelt es sich um einen Wert, der den Sitzungs-Debug-Manager eindeutig identifiziert, der ursprünglich an diesen Prozess angefügt wurde. keine der Methoden der angegebenen Schnittstelle ist funktionsfähig.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
