---
description: Diese Methode informiert den Prozess, dass eine Sitzung jetzt den Prozess debuggt.
title: 'IDebugProcessEx2:: Attach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149742"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Diese Methode informiert den Prozess, dass eine Sitzung jetzt den Prozess debuggt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parameter
`pSession`\
in Ein-Wert, der die Sitzung, die an diesen Prozess angehängt wird, eindeutig identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die übergebene Schnittstelle `pSession` muss nur als Cookie behandelt werden. dabei handelt es sich um einen Wert, der den Sitzungs-Debug-Manager eindeutig identifiziert, der an diesen Prozess angehängt wird. keine der Methoden der angegebenen Schnittstelle ist funktionsfähig.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
