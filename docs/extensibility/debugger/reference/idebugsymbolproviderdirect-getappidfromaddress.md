---
title: 'Idebugsymbolproviderdirect:: getappidfromaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfdc81b18b68a3dafe239bb2f23f700f9796cf8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909551"
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
Ruft den Anwendungs Domänen Bezeichner anhand der debugadresse ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAppIDFromAddress(
   IDebugAddress* pAddress,
   DWORD*         pAppID
);
```

```csharp
int GetAppIDFromAddress(
   IDebugAddress pAddress,
   out uint      pAppID
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Debug-Adresse, die durch die [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird.

`pAppID`\
vorgenommen Der Bezeichner der Anwendungsdomäne.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
