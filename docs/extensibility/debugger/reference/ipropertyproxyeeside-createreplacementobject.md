---
description: Erstellt eine Kopie eines Datenobjekts, das spezifisch für die-Ausdrucks Auswertung (EE) ist.
title: 'Ipropertyproxyeeside:: kreatereplacementobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 341ca3d00a433c4bb36bc22ab2d598d7b454842a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225707"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Erstellt eine Kopie eines Datenobjekts, das spezifisch für die-Ausdrucks Auswertung (EE) ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataIn`\
in Ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das die zu kopierenden Daten enthält.

`dataOut`\
[out] Gibt ein neues `IEEDataStorage`-Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erhält ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, das ein Bytearray darstellt. Dieses eingehende Datenobjekt wird in der Regel nicht von EE implementiert. Allerdings wird das von dieser Methode zurückgegebene-Objekt immer von der EE implementiert, sodass das EE die- `IEEDataStorage` Schnittstelle für jede gewünschte Klasse implementieren kann.

 Beachten Sie, dass die vom eingehenden Objekt bereitgestellten Daten `IEEDataStorage` die gleichen Daten im ausgehenden Objekt sein müssen `IEEDataStorage` .

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
