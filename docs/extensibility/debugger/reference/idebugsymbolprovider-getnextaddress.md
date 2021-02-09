---
title: 'Idebugsymbolprovider:: getnextaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a370cf4591146a31627b80f6358a3d3f9202e306
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888224"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Ruft die debugadresse ab, die einer bestimmten debugadresse in einer Methode folgt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Die angegebene debugadresse.

`fStatementOnly`\
in Wenn true, werden die debugadressen auf eine einzige Anweisung beschränkt.

`ppAddress`\
vorgenommen Gibt die nächste debugadresse zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt einen gültigen zurück `HRESULT` , in der Regel S_OK.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
