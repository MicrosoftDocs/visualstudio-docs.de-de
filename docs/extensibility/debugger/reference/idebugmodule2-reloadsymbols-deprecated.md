---
description: VERALTET. Lädt die Symbole für dieses Modul erneut.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d07f80a3dccef666c0608d79505816f73ff52013
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150522"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
VERALTET. Verwenden Sie nicht. Lädt die Symbole für dieses Modul erneut.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parameter
`pszUrlToSymbols`\
in Der Pfad zum Symbol Speicher.

`pbstrDebugMessage`\
vorgenommen Gibt eine Informations Meldung zurück, z. b. einen Status oder eine Fehlermeldung, die rechts neben dem Modulnamen im Fenster "Module" angezeigt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Eine Debug-Engine sollte immer zurückgeben `E_FAIL` .

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird nicht mehr unterstützt. Implementieren Sie stattdessen die [loadsymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) -Methode.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
