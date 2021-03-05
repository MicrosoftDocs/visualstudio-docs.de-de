---
description: Ruft die debugadresse ab, die einer bestimmten debugadresse in einer Methode folgt.
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
ms.openlocfilehash: d177d03daef4f8d3344941658b85f71551af126b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168412"
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
