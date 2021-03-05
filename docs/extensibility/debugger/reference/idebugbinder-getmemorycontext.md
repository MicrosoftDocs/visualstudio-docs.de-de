---
description: Diese Methode konvertiert entweder einen Objekt Speicherort oder eine Speicheradresse in einen Speicher Kontext.
title: 'Idebugbinder:: getmemorycontext | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e31df905c35fa81e3e56e32ef969f9663054dc5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174093"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Diese Methode konvertiert entweder einen Objekt Speicherort oder eine Speicheradresse in einen Speicher Kontext.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parameter
`pField`\
in Ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) , das das zu suchende Objekt beschreibt. Wenn `NULL` , dann verwenden Sie `dwConstant` stattdessen.

`dwConstant`\
in Eine Konstante Speicheradresse, z. b. 0x5.000.

`ppMemCxt`\
vorgenommen Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Schnittstelle zurück, die die Adresse des-Objekts darstellt, oder die Adresse im Arbeitsspeicher.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
