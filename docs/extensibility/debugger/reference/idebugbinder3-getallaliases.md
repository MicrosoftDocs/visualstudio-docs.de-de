---
title: 'IDebugBinder3:: getallaliases | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea8de97a82959b1135866988aeeeb14cf464e8b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925083"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Diese Methode ruft eine Liste von Aliasen aus dem Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parameter
`uRequest`\
in Die maximale Anzahl von Aliasen, die zurückgegeben werden sollen (gibt die Länge des an übergebenen Arrays an `ppAliases` ).

`ppAliases`\
[in, out] Array, das mit Aliasen ausgefüllt werden soll (wenn es sich um einen NULL-Wert handelt und `uRequest` 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, von zurückgegeben `puFetched` ).

`puFetched`\
vorgenommen Gibt die Anzahl der abgewonnenen Aliase zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
