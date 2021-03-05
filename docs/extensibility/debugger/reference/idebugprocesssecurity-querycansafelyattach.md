---
description: Mit dieser Methode kann der Port Lieferant eine Warnung anzeigen, bevor der Benutzer an einen unsicheren Prozess angefügt wird.
title: 'Idebugprocesssecurity:: querycansafelyattach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166163"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Mit dieser Methode kann der Port Lieferant eine Warnung anzeigen, bevor der Benutzer an einen unsicheren Prozess angefügt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Rückgabewert
 Die Rückgabewerte lauten wie folgt:

- `S_OK`: Das Anhängen an den Prozess ist sicher, und es wird kein Warn Dialogfeld angezeigt.

- `S_FALSE`: Das Anfügen kann ein Sicherheitsproblem sein, und es wird ein Dialogfeld mit einer Warnung angezeigt.

- `FAILURE`: Fehler beim Anhängen an den Prozess.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
