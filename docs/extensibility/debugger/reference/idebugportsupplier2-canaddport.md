---
description: Hiermit wird überprüft, ob ein Port Lieferant neue Ports hinzufügen kann.
title: 'IDebugPortSupplier2:: canaddport | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c53abba81b02aa6125d4fa25ce16db85579ce5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142660"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Hiermit wird überprüft, ob ein Port Lieferant neue Ports hinzufügen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Rückgabewert
 Wenn der Port hinzugefügt werden kann, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` um anzugeben, dass diesem Port Lieferanten keine Ports hinzugefügt werden können.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, bevor Sie die [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) -Methode aufrufen, da die zweite Methode den Port erstellt und hinzugefügt wird, was möglicherweise ein zeitaufwendiger Vorgang ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
