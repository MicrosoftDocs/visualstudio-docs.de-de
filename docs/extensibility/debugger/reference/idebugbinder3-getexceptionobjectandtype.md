---
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
ms.openlocfilehash: ee86b12b16cc76b8e2c06ede5ec0110322b515ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891227"
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
