---
description: Diese Methode ändert das Objekt, das die Schnellansicht darstellt.
title: 'Ieevisualizerdataprovider:: setobjectforvisualizer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df5cfd2acef1a2214d4692a49c742c26cd420ffa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227228"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Diese Methode ändert das Objekt, das die Schnellansicht darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parameter
`pNewObject`\
in Das festzulegende-Objekt.

`error`\
vorgenommen Wenn beim Festlegen des-Objekts ein Fehler aufgetreten ist, enthält diese Zeichenfolge die Fehlermeldung.

`pException`\
vorgenommen Wenn ein Fehler aufgetreten ist, enthält dieses Objekt die Ausnahme Informationen.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es ist für den Implementierer festzulegen, wie Fehlerinformationen zurückgegeben werden. Es ist jedoch möglich, dass einige Aufrufer nur überprüfen, ob ein Ausnahme Objekt zurückgegeben wurde, um zu wissen, dass ein Fehler aufgetreten ist. Daher sollte diese Methode immer ein Ausnahme Objekt zurückgeben, wenn ein Fehler aufgetreten ist. Die Fehler Zeichenfolge sollte auch für den Fall bereitgestellt werden, dass der Aufrufer Sie verwenden möchte.

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
