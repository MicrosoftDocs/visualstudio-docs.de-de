---
description: Diese Methode erhält den Namen der Enumerationskonstante, wenn ihr Wert angegeben wird.
title: 'Idebugenenfield:: getstringfromvalue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8601be6a1c87fcad10c6e5260e791fcf2ce42f01
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153338"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Diese Methode erhält den Namen der Enumerationskonstante, wenn ihr Wert angegeben wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parameter
`value`\
in Der Wert, für den der Name der Enumerationskonstante angezeigt werden soll.

`pbstrValue`\
vorgenommen Gibt den Namen der Enumerationskonstante zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` Wenn der Wert keinen zugeordneten Namen hat, oder es wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn dem gleichen Wert mehr als ein Name zugeordnet ist, wird der Vorname zurückgegeben, der in der-Enumeration definiert ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
