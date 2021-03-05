---
description: Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debug-Engine.
title: 'Idebugobject:: getmanageddebugobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87956b3630f9d152ecdda7754623e7257cf0a01a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164764"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debug-Engine.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ppObject`\
vorgenommen Gibt ein [idebugmanagedobject](../../../extensibility/debugger/reference/idebugmanagedobject.md) -Objekt zurück, das das neu erstellte verwaltete-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) keine Instanz einer verwalteten Wert Klasse darstellt.

## <a name="remarks"></a>Bemerkungen
 Dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt muss eine Instanz der verwalteten Wert Klasse, z. b. eine-Instanz, darstellen `System.Decimal` . Wenn eine lokale Kopie vorhanden ist, wird der Aufwand für das Aufrufen von [Evaluierungen](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) vermieden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
