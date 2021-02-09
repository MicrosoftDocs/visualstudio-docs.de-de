---
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
ms.openlocfilehash: 03c2ab7b701163e22a5cc3ff386f447c5199ff15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892566"
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
