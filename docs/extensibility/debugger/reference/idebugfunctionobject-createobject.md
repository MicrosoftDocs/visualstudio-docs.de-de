---
description: Erstellt ein-Objekt mithilfe eines Konstruktors.
title: 'Idebugfunctionobject:: kreateobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8870910e01f2afa5bff6eac461d6e80f35e6a7e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150041"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Erstellt ein-Objekt mithilfe eines Konstruktors.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parameter
`pConstructor`\
in Ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt, das den Konstruktor des zu erstellenden Objekts darstellt.

`dwArgs`\
in Die Anzahl der Parameter im `pArg` Array. Stellt die Anzahl von Parametern dar, die an den Konstruktor übergeben werden.

`pArg`\
in Ein Array von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten, das die Parameter darstellt, die an den Konstruktor übergeben werden.

`ppObject`\
vorgenommen Gibt ein zurück, `IDebugObject` das das neu erstellte-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Klasse (oder einen anderen komplexen Typ, der einen Konstruktor erfordert) darstellt, bei dem es sich um einen Parameter für die Funktion handelt, die durch die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle dargestellt wird

 Wenn für den Object-Parameter kein Konstruktor erforderlich ist, müssen Sie die Methode "up- [objectnoconstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) " aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
