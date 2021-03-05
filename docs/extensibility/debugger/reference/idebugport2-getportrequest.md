---
description: Ruft die Beschreibung eines Ports ab, der zuvor zum Erstellen des Ports verwendet wurde (falls verfügbar).
title: 'IDebugPort2:: getportrequest | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 084e8bb94356ea4e2cff1fa83e83e7e08b35134e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142868"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ruft die Beschreibung eines Ports ab, der zuvor zum Erstellen des Ports verwendet wurde (falls verfügbar).

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parameter
`ppRequest`\
vorgenommen Gibt ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Objekt zurück, das die Anforderung darstellt, die zum Erstellen des Ports verwendet wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  Gibt zurück, `E_PORT_NO_REQUEST` Wenn ein Port nicht mithilfe einer [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Port Anforderung erstellt wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
