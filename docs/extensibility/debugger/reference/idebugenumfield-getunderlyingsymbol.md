---
title: 'Idebugenenfield:: getunderlyingsymbol | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c812117e59ca50e64fa6e987ebbe1d30d8d552c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933530"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Diese Methode gibt ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen der Enumeration darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt das [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen dieser Enumeration beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Name der-Enumeration enthält auch den Typ der-Enumeration, der mithilfe von [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)an eine Speicheradresse gebunden wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)
