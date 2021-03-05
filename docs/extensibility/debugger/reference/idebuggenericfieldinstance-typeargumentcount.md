---
description: Gibt die Anzahl der Typparameter Argumente für diese Instanz zurück.
title: 'Idebuggenericfieldinstance:: typeargumentcount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 034c180e41a2754347dd0eea7a81cb4ae64a0c2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165357"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Gibt die Anzahl der Typparameter Argumente für diese Instanz zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parameter
`pcArgs`\
[in, out] Anzahl der Typparameter Argumente für diese Instanz.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn z. b. List \<int> lautet, gibt diese Methode 1 zurück, und, wenn List, \<int,float2> gibt diese Methode 2 zurück. Diese Methode gibt 0 zurück, wenn keine Typargumente vorhanden sind.

## <a name="see-also"></a>Weitere Informationen
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
