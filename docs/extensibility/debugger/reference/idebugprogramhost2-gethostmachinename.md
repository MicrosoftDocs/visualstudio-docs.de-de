---
description: Ruft den Namen des Computers ab, auf dem der Prozess ausgeführt wird, auf dem dieses Programm gehostet wird.
title: 'IDebugProgramHost2:: gethostmachinename | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5ba8a2598af54f700ec85f3e3856b29166f2613
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145247"
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Ruft den Namen des Computers ab, auf dem der Prozess ausgeführt wird, auf dem dieses Programm gehostet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostMachineName( 
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName( 
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parameter
`pbstrHostMachineName`\
vorgenommen Gibt den Namen des Computers zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
