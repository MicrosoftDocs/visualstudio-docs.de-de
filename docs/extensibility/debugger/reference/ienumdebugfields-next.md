---
description: Diese Methode gibt den nächsten Satz von Elementen aus der Fields-Enumeration zurück.
title: 'Ienumentbugfields:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb60dcf991c1a3002612b6779ef179c1571f3244
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226656"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
Diese Methode gibt den nächsten Satz von Elementen aus der-Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe des `rgelt` Arrays an.

`rgelt`\
[in, out] Array der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Elemente, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Gibt die Anzahl der Elemente zurück, die tatsächlich in zurückgegeben werden `rgelt` .

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden kann. andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
