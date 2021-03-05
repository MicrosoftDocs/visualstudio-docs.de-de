---
description: Diese Methode verwendet die Suche ohne Beachtung der Groß-/Kleinschreibung, um den Wert zurückzugeben, der dem Namen einer Enumerationskonstante zugeordnet ist
title: 'Idebugenenfield:: getvaluefromstringcaseinsensitive | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f853598c5d3c9b293c806e1db475c5053a1a208e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153221"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Diese Methode verwendet die Suche ohne Beachtung der Groß-/Kleinschreibung, um den Wert zurückzugeben, der dem Namen einer Enumerationskonstante zugeordnet ist

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
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
 Bei dieser Methode wird Groß-/Kleinschreibung nicht beachtet. Wenn eine Suche nach Groß-/Kleinschreibung erforderlich ist (z. b. in einer Sprache wie C++, bei der bei Namen die Groß-/Kleinschreibung beachtet wird), verwenden Sie [getvaluefromstring](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
