---
description: Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.
title: 'Idebugarrayfield:: GetRank | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9e3d822bac6fa16314f5d2962d69adbf74d0bc3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143713"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parameter
`pdwRank`\
vorgenommen Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Rang eines Arrays entspricht der Anzahl von Dimensionen. In C++ und c# sind mehrdimensionale Arrays tatsächlich Arrays von Arrays und können daher nur als eindimensionales Array betrachtet werden (und die `GetRank` Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] werden mehrdimensionale Arrays unterschiedlich behandelt, und der Rang eines solchen Arrays spiegelt die Anzahl der Dimensionen wider (und die- `GetRank` Methode gibt immer die Anzahl der Dimensionen zurück).

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
