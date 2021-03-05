---
description: Fügt einen Port hinzu.
title: 'IDebugPortSupplier2:: AddPort | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14232ac49b3862c635a41c25e79c7ab166fa24ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169235"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Fügt einen Port hinzu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parameter
`pRequest`\
in Ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Objekt, das den hinzu zufügenden Port beschreibt.

`ppPort`\
vorgenommen Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Objekt zurück, das den Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erstellt tatsächlich den angeforderten Port und fügt ihn der internen Liste aktiver Ports des Port Anbieters hinzu. Die [canaddport](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) -Methode kann zuerst aufgerufen werden, um mögliche zeitaufwändige Verzögerungen zu vermeiden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
