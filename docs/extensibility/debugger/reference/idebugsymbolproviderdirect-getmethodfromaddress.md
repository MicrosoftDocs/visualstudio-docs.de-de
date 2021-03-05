---
description: Ruft Informationen zur Methode an der angegebenen debugadresse ab.
title: 'Idebugsymbolproviderdirect:: getmethodfromaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dea6367280217f42238a56a56a6ce0e0e6f92b47
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149495"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Ruft Informationen zur Methode an der angegebenen debugadresse ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Debug-Adresse, die durch die [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird.

`pGuid`\
vorgenommen Eindeutiger Bezeichner des Moduls.

`pAppID`\
vorgenommen Der Bezeichner der Anwendungsdomäne.

`pTokenClass`\
vorgenommen Token, das die enthaltende Klasse darstellt.

`pTokenMethod`\
vorgenommen Token, das das Modul darstellt.

`pdwOffset`\
vorgenommen Ein Offset in Bytes vom Anfang des- `pAddress` Parameters.

`pdwVersion`\
vorgenommen Versionsnummer der Methode.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
