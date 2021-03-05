---
description: Diese Methode ruft Anzeigeinformationen über das Feld ab.
title: 'Idebugfield:: GetInfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c681fef38377f0ce8e74b45dba065b5eae39462c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151934"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Diese Methode ruft Anzeigeinformationen über das Feld ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
in Eine Kombination aus [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Konstanten, die die anzuzeigenden Informationen auswählt. Wenn das Feld ein Symbol darstellt, ist dies in der Regel der Symbol Name und-Typ.

`pFieldInfo`\
vorgenommen Gibt die Informationen in der bereitgestellten [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) -Struktur zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
