---
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
ms.openlocfilehash: 2ba5456ba3beabb1d5418d739be2aa74838daa41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947176"
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
