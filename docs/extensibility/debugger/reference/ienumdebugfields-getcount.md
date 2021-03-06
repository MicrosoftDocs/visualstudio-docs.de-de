---
description: Diese Methode gibt die Anzahl der Elemente in der Fields-Enumeration zurück.
title: 'Ienumentbugfields:: GetCount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dbce3c9f990e28b63ca3b600e89d12736021dbf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226643"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
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
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
