---
description: Ruft den Prozess Bezeichner des Prozesses ab, der dieses Programm gehostet.
title: 'IDebugProgramHost2:: gethostid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9784c8e54ee5c75ed33a0aaf513f71dd09f6191
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168126"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Ruft den Prozess Bezeichner des Prozesses ab, der dieses Programm gehostet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostId( 
   AD_PROCESS_ID* pdwId
);
```

```csharp
int GetHostId( 
   AD_PROCESS_ID[] pdwId
);
```

## <a name="parameters"></a>Parameter
`pdwId`\
[in, out] Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die mit den Prozess-ID-Informationen aufgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
