---
description: Diese Methode gibt den Typ des Objekts zurück, auf das dieses Zeiger Objekt zeigt.
title: 'Idebugpointerfield:: getdereferencedfield | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 765ad40be87b7700ca1087745bef43ff0575dfa6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169703"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Diese Methode gibt den Typ des Objekts zurück, auf das dieses Zeiger Objekt zeigt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Typ des Zielobjekts beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn das [idebugpointerfield](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt z. b. auf eine ganze Zahl zeigt, beschreibt der von dieser Methode zurückgegebene [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Typ diesen ganzzahligen Typ.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
