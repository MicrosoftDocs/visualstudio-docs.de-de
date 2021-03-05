---
description: Legt das Gebiets Schema der Debug-Engine (de) fest.
title: 'IDebugEngine2:: setlocale | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cfd2d9d51cbad414cfb481b88f1e3277500efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153910"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Legt das Gebiets Schema der Debug-Engine (de) fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parameter
`wLangID`\
in Gibt das Gebiets Schema der Sprache an. Beispiel: 1033 für Englisch.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird vom Sitzungs-Debug-Manager (SDM) aufgerufen, um die Gebiets Schema Einstellungen der IDE zu übertragen, sodass von der de zurückgegebene Zeichen folgen ordnungsgemäß lokalisiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
