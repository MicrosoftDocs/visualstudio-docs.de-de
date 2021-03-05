---
description: Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.
title: 'Idebugmethodfield:: iscustomattributedefined | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c78e8fb22f78cdb97bd57ee67cfc20cd19f0bde
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164902"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parameter
`pszCustomAttributeName`\
in Eine Zeichenfolge mit dem Namen des zu suchenden benutzerdefinierten Attributs.

## <a name="return-value"></a>Rückgabewert
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für diese Methode definiert ist; andernfalls wird S_FALSE zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
