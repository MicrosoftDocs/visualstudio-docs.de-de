---
title: 'Idebugenenfield:: getvaluefromstring | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77cce7a6780c816fbee0ade1c795cb1174e3e7f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933452"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Diese Methode gibt den Wert zurück, der dem Namen einer Enumerationskonstante zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parameter
`pszValue`\
in Eine Zeichenfolge, die den Namen angibt, für den der Wert zu erhalten ist. Beachten Sie, dass dies für C++ eine Zeichenfolge mit breit Zeichen ist.

`pValue`\
vorgenommen Gibt den zugeordneten numerischen Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` , wenn der Name nicht Teil der-Enumeration ist, oder ein Fehlercode.

## <a name="remarks"></a>Bemerkungen
 Bei dieser Methode wird die Groß-/Kleinschreibung beachtet. Wenn eine Suche ohne Berücksichtigung der Groß-/Kleinschreibung erforderlich ist (z. b. in einer Sprache wie Visual Basic, in der die Groß-/Kleinschreibung nicht beachtet wird), verwenden Sie [getvaluefromstringcaseinsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
