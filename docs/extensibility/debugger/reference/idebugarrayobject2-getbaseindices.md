---
description: Ruft die Basis Indizes (untere Grenzen) für jeden Index ab, wenn die Anzahl der Dimensionen im Array angegeben wird.
title: 'IDebugArrayObject2:: getbaseindices | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3ec8c0081205637ae228c426ac29d0523602439
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167788"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Ruft die Basis Indizes (untere Grenzen) für jeden Index ab, wenn die Anzahl der Dimensionen im Array angegeben wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Parameter
`dwRank`\
in Die Anzahl der Dimensionen (Rang) des Arrays.

`dwIndices`\
vorgenommen Die Basis Indizes (untere Begrenzungen) für das Array.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Funktion würde z. b. "5" für das Array zurückgeben, das durch den folgenden c#-Code erstellt wurde:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
