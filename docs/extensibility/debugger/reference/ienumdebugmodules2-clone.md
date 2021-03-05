---
description: Gibt eine Kopie der aktuellen Modul Enumeration als separates Objekt zurück.
title: 'IEnumDebugModules2:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 699afcaabdf88ca8b2b6ea60b6ad06dfcb12e3bd
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224888"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Gibt eine Kopie der aktuellen Enumeration als ein separates Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Clone(
   IEnumDebugModules2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugModules2 ppEnum
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
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
