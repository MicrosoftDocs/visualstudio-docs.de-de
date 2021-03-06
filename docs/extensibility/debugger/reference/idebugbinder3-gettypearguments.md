---
description: Diese Methode ruft eine Liste von Argument Typen ab, die diesem-Objekt zugeordnet sind.
title: 'IDebugBinder3:: gettypeer Arguments | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74cbd6e67a82113e43226ded8640630be50ba086
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173896"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Diese Methode ruft eine Liste von Argument Typen ab, die diesem-Objekt zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parameter
`skip`\
in Anzahl der Felder, die vor dem erhalten von Argument Typen übersprungen werden.

`count`\
in Die Anzahl der zurück zugebende Argument Felder (gibt auch die Größe des `ppFields` Arrays an).

`ppFields`\
[in, out] Ein Array von Feldern, die bei der Rückgabe dieser Methode ausgefüllt werden.

`pFetched`\
[out] \( optional) die Anzahl der Argumenttyp Felder, die tatsächlich zurückgegeben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Anzahl von Argument Typen kann im Voraus mit [gettyetargumentcount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)abgerufen werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
