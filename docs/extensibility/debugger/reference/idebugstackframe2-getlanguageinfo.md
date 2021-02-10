---
title: 'IDebugStackFrame2:: getlanguageingefo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7e9b08847ea4d0c513ea458bd1ab40211cb9515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956528"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Ruft die Sprache ab, die diesem Stapel Rahmen zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parameter

`pbstrLanguage`\
vorgenommen Gibt den Namen der Sprache zurück, die die diesem Stapel Rahmen zugeordnete Methode implementiert.

`pguidLanguage`\
vorgenommen Gibt den `GUID` der Sprache zurück. Für die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Sprachen kann beispielsweise Folgendes zurückgegeben werden:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Rückgabewert

 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
