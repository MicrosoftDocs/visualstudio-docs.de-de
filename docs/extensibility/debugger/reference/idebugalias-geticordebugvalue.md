---
description: Ruft eine verwaltete Code Schnittstelle ab, die den diesem Alias zugeordneten Wert darstellt.
title: 'Idebugalias:: geticorentbugvalue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b809e16fefb9306da842f39d93bdb3dd0f7b404f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143934"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Ruft eine verwaltete Code Schnittstelle ab, die den diesem Alias zugeordneten Wert darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parameter
`ppUnk`\
[out] `IUnknown` eine Schnittstelle, die den diesem Alias zugeordneten Wert darstellt. Diese Schnittstelle kann für die-Schnittstelle abgefragt werden `ICorDebugValue` .

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode gilt nur für verwaltete Werte ( `ICorDebugValue` ist eine Schnittstelle, die in der .NET Framework verfügbar ist und im .NET Framework SDK in der Datei "Cordebug. idl" definiert ist).

## <a name="see-also"></a>Weitere Informationen
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
