---
title: 'IDebugCodeContext2:: getlanguageingefo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6719968d2e828340b16f84f3195f722803d8d9d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928730"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ruft die Sprachinformationen für diesen Code Kontext ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parameter
`pbstrLanguage`\
[in, out] Gibt eine Zeichenfolge zurück, die den Namen der Sprache enthält, z. b. "C++".

`pguidLanguage`\
[in, out] Gibt die GUID für die Sprache des Code Kontexts zurück, z `guidCPPLang` . b..

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mindestens einer der Parameter muss einen Wert ungleich NULL zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
