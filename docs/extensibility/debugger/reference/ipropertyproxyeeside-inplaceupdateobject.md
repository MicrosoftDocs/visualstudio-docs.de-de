---
title: 'Ipropertyproxyeeside:: inplaceupdateobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f8185734c8c2ee15728328a510236bbbc50a21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895972"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualisiert die Daten des Objekts mit dem angegebenen Datenobjekt und gibt ein neues Datenobjekt zurück, das die neuen Daten des Objekts darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataIn`\
in Ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das die neuen Daten enthält.

`dataOut`\
vorgenommen Gibt ein neues-Objekt zurück, `IEEDataStorage` das die ersetzten Daten enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode aktualisiert tatsächlich die Daten des Objekts. Die Daten im zurückgegebenen [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt müssen nicht mit den Daten im eingehenden Objekt identisch sein `IEEDataStorage` , aber das zurückgegebene Objekt muss den aktuellen Wert der Eigenschaft widerspiegeln.

 Das eingehende Datenobjekt wird in der Regel nicht vom EE implementiert. Allerdings wird das von dieser Methode zurückgegebene-Objekt immer von der EE implementiert, sodass das EE die- `IEEDataStorage` Schnittstelle für jede gewünschte Klasse implementieren kann.

 Die Methode " [kreatereplacementobject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) " erstellt ein Datenobjekt auf Grundlage des eingehenden Datenobjekts, wirkt sich jedoch nicht auf die ursprünglichen Daten der Eigenschaft aus.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
