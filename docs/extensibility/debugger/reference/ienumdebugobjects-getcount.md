---
description: Diese Methode gibt die Anzahl der idebugobject-Elemente in der-Enumeration zurück.
title: 'Ienumdebugobjects:: GetCount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54247fd49792b0a0ce5ed3218429b97b0ccdfcbf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224680"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Diese Methode gibt die Anzahl der Elemente in der-Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parameter
`pcelt`\
vorgenommen Gibt die Anzahl der Elemente in der-Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Teil der üblichen com-Enumerationsschnittstelle, die angibt, dass nur "Next", "Clone", "Skip" und "Reset" implementiert werden müssen.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
