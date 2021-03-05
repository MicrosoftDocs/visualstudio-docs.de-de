---
description: Ruft die übergeordnete Eigenschaft einer Eigenschaft ab.
title: 'IDebugProperty2:: GetParent | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae5557734ab59a2e71a67404a50519d72ca1ec0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166826"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Ruft die übergeordnete Eigenschaft einer Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Parameter
`ppParent`\
vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das das übergeordnete Element der Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Gibt `S_GETPARENT_NO_PARENT` zurück, wenn kein übergeordnetes Element vorhanden ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
