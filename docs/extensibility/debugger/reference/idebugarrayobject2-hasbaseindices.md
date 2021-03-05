---
description: Bestimmt, ob für das Array Basis Indizes (untere Begrenzungen) definiert sind.
title: 'IDebugArrayObject2:: hasbaseindices | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6f140efbb28545e7efc06461265fd83f4f533d1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143674"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Bestimmt, ob für das Array Basis Indizes (untere Begrenzungen) definiert sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>Parameter
`pfHasBaseIndices`\
vorgenommen TRUE, um anzugeben, dass das Array über Basis Indizes (untere Begrenzungen) verfügt; andernfalls false.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.
