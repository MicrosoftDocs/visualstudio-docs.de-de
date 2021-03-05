---
description: Diese Methode vergleicht dieses Feld mit dem angegebenen Feld auf Gleichheit.
title: 'Idebugfield:: Equal | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2bf9b3e4bbb988621e3b65e855b07322fba1795
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152090"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Diese Methode vergleicht dieses Feld mit dem angegebenen Feld auf Gleichheit.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parameter
`pField`\
in Das Feld, das mit diesem verglichen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Felder identisch sind, wird zurückgegeben `S_OK` . Wenn die Felder verschieden sind, wird zurückgegeben `S_FALSE.` , andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
