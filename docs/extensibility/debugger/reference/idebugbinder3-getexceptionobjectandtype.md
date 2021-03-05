---
description: Diese Methode ruft die Ausnahme ab, die einem Objekt zugeordnet ist, sofern vorhanden.
title: 'IDebugBinder3:: getexceptionobjectandtype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ec511cc6145c890c4f62a76563c51aa7c667977
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167632"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Diese Methode ruft die Ausnahme ab, die einem Objekt zugeordnet ist, sofern vorhanden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parameter
`ppException`\
vorgenommen Gibt das-Objekt zurück, das die Ausnahme darstellt.

`ppField`\
vorgenommen Gibt das-Objekt zurück, das ein bestimmtes Feld darstellt, das möglicherweise die Ausnahme verursacht hat (Dies kann ein NULL-Wert sein).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Um zu überprüfen, ob eine Ausnahme vorliegt, überprüfen Sie den von zurückgegebenen Wert `ppException` : Wenn es sich um einen NULL-Wert handelt, wird diesem-Objekt keine Ausnahme zugeordnet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
