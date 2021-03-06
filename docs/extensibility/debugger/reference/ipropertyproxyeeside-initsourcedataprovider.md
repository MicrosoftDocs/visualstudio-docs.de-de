---
description: Initialisiert die Quelldaten für dieses-Objekt und gibt ein-Objekt zurück, das die Anfangsdaten enthält.
title: 'Ipropertyproxyeeside:: initsourcedataprovider | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd1040c6269b9d394e6f0968f595c71cf1576135
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224121"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Initialisiert die Quelldaten für dieses-Objekt und gibt ein-Objekt zurück, das die Anfangsdaten enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataOut`\
vorgenommen Gibt ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode übernimmt alle Elemente, die zum Initialisieren eines Objekts erforderlich sind, damit eine [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle für die Daten des Objekts zurückgegeben werden kann. Dadurch können die Daten des Objekts angezeigt und, falls zulässig, von einer typschnell Ansicht geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
