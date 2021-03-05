---
description: Teilt dem Programm-oder Programmknoten mit, welches Debug-Modul (de) zum Debuggen dieses Programms verwendet werden soll.
title: 'IDebugProgramEngines2:: abtengine | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17e990731059d4cee6e5f716c74edf93e13b87fb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161410"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Teilt dem Programm-oder Programmknoten mit, welches Debug-Modul (de) zum Debuggen dieses Programms verwendet werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parameter
`guidEngine`\
in Der GUID der de.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
