---
title: 'IDebugPortRequest2:: getportname | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 574ea2ecb69c944bdb47ff80d7b4e26db51933da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887158"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ruft den Namen des Ports ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parameter
`pbstrPortName`\
vorgenommen Gibt den Namen des Ports zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Schnittstelle wird normalerweise von einem Debugpaket (dem-Client) an einen Port Lieferanten (den-Server) weitergegeben, um eine Verbindung mit einem Port herzustellen. Sowohl das Debugpaket als auch der Port Lieferant kennen die möglichen Optionen für den Port. Wenn eine einfache Zeichenfolge den Port beschreiben kann, `IDebugPortRequest2::GetPortName` verfügt die Methode über ausreichend Informationen, um die Verbindung herzustellen. Andernfalls können zusätzliche Schnittstellen vom Client bereitgestellt werden, der vom Server mithilfe von abgerufen werden kann `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
