---
title: 'IDebugPortSupplier3:: enumpersistedports | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09b1fabaeb5bf887eedaa53d57bdeb3604bf2257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840326"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Diese Methode ruft ein Objekt ab, das die Enumeration der Liste der persistenten Ports zulässt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`PortNames`\
in Eine [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Struktur, die eine Liste von Portnamen enthält, die gefunden und zwischen den beibehaltenen Ports zurückgegeben werden sollen. Nur die persistenten Ports mit diesen Namen werden zurückgegeben.

`ppEnum`\
vorgenommen Ein Objekt, das die [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) -Schnittstelle implementiert.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Persistente Ports werden geladen, wenn ein Port Lieferant instanziiert wird, und werden gespeichert, wenn der Port Lieferant zerstört wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
