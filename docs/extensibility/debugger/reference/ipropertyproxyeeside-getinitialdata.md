---
title: 'Ipropertyproxyeeside:: getinitialdata | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetInitialData
helpviewer_keywords:
- IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed7a3b72f35c21c61bd805a45307a98556208d72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852801"
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
Gibt die Anfangsdaten für dieses-Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInitialData(
   IEEDataStorage** dataOut
);
```

```csharp
int GetInitialData(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataOut`\
vorgenommen Gibt ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt zurück, das die ursprünglichen Daten dieses Objekts enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
