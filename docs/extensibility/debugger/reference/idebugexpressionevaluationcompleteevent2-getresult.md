---
description: Ruft das Ergebnis der Ausdrucks Auswertung ab.
title: 'IDebugExpressionEvaluationCompleteEvent2:: GetResult | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00200c9aaa23249eefc4b1b6d0876065ce1ed4ad
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152610"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Ruft das Ergebnis der Ausdrucks Auswertung ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>Parameter
`ppResult` vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das das Ergebnis der Ausdrucks Auswertung darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das zurückgegebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt enthält den Wert des ausgewerteten Ausdrucks. Beachten Sie, dass es sich bei diesem Wert um einen komplexen Wert, z. b. ein Array, handeln kann, das Endergebnis jedoch ein numerischer Wert oder ein Zeichen folgen Wert sein muss

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
