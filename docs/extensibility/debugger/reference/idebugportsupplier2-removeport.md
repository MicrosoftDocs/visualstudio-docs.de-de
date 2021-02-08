---
title: 'IDebugPortSupplier2:: RemovePort | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192bee4a40adb9f876b4d7c7812b10c357972ace
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840352"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Entfernt einen Port.

## <a name="syntax"></a>Syntax

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

## <a name="parameters"></a>Parameter
`pPort`\
in Ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Objekt, das den zu entfernenden Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mit dieser Methode wird der Port aus der internen Liste aktiver Ports des Port Anbieters entfernt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
