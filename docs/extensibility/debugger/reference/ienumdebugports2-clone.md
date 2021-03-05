---
description: Gibt eine Kopie der aktuellen Ports-Enumeration als separates Objekt zurück.
title: 'IEnumDebugPorts2:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Clone
helpviewer_keywords:
- IEnumDebugPorts2::Clone
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c67f5db40ceae230e11c7aa3f3868553aa60b49b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226331"
---
# <a name="ienumdebugports2clone"></a>IEnumDebugPorts2::Clone
Gibt eine Kopie der aktuellen Enumeration als ein separates Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Clone(
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Kopie der-Enumeration hat denselben Zustand wie die ursprüngliche, wenn diese Methode aufgerufen wird. Allerdings sind die Status der Kopier-und ursprünglichen Zustände getrennt und können einzeln geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
