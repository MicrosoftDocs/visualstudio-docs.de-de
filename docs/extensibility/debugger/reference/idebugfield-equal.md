---
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
ms.openlocfilehash: c19e8860fb9ed9cbd65efe7fa72fd920a01622ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915476"
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
