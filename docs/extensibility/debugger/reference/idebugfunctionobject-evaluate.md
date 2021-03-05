---
description: 'Idebugfunctionobject:: Evaluation Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.'
title: 'Idebugfunctionobject:: evaluieren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d15cdb09de32edcdf6159567db12e05cffd06e7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160107"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
in Ein Array von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten, die die Eingabeparameter darstellen. Jeder dieser Parameter wurde mit einer der- `Create` Methoden in der [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle erstellt.

`dwParams`\
in Die Anzahl der Parameter im `ppParams` Array.

`dwTimeout`\
in Gibt die maximale Zeit in Millisekunden an, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

`ppResult`\
vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das den Wert der Funktion als Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode richtet einen Aufruf der Funktion ein, die vom [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt dargestellt wird, und führt Sie aus.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
