---
title: 'Idebugcustomattribute:: GetName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5aade49d77861d6aacdf955a167aeccbbaca4071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928431"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ruft den Namen des benutzerdefinierten Attributs ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parameter
`bstrName`\
vorgenommen Gibt eine Zeichenfolge zurück, die den Namen des benutzerdefinierten Attributs enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der von dieser Methode zurückgegebene benannte entspricht dem Namen der Klasse, die verwendet wird, um das Attribut zu deklarieren. Dies entspricht möglicherweise nicht exakt dem Namen der benutzerdefinierten Attribut Klasse, da c# es zulässt, dass das Suffix "Attribute" aus einem benutzerdefinierten Attributnamen gelöscht wird, wenn es in einer Deklaration verwendet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
