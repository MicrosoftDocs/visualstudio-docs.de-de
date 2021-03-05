---
description: Vergleicht den Speicher Kontext mit jedem Kontext im angegebenen Array in der durch Compare-Flags angegebenen Weise, wobei ein Index des ersten Kontexts zurückgegeben wird, der entspricht.
title: 'IDebugMemoryContext2:: Compare | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f21b22574a780f5e9fcfa045c6786b13d82caa45
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165097"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Vergleicht den Speicher Kontext mit jedem Kontext im angegebenen Array in der durch Compare-Flags angegebenen Weise, wobei ein Index des ersten Kontexts zurückgegeben wird, der entspricht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parameter
`compare`\
in Ein Wert aus der [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) Enumeration, der den Typ des Vergleichs bestimmt.

`rgpMemoryContextSet`\
in Ein Array von Verweisen auf die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekte, mit denen verglichen werden soll.

`dwMemoryContextSetLen`\
in Die Anzahl der Kontexte im `rgpMemoryContextSet` Array.

`pdwMemoryContext`\
vorgenommen Gibt den Index des ersten Speicher Kontexts zurück, der den Vergleich erfüllt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_COMPARE_CANNOT_COMPARE` Wenn die beiden Kontexte nicht verglichen werden können.

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine (de) muss nicht alle Typen von vergleichen unterstützen, muss jedoch mindestens `CONTEXT_EQUAL` , und unterstützen `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
