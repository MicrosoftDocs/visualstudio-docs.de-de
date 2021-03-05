---
description: Ruft die Methode ab, die die-Eigenschaft festlegt.
title: 'Idebugpropertyfield:: getpropertysetter | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd787b88ae0e45de7afe944a79fdd0a788aa1449
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167931"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Ruft die Methode ab, die die-Eigenschaft festlegt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt zurück, das die Methode darstellt, die die-Eigenschaft festlegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um die Methode abzurufen, die die Eigenschaft abruft, können Sie die [getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
