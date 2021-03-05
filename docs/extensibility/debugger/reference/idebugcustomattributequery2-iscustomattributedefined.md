---
description: Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.
title: 'IDebugCustomAttributeQuery2:: iscustomattributedefined | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c25a0357a1b0b8768f02fd7eb903c30943964445
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168295"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.

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
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für dieses Feld definiert ist, andernfalls wird S_FALSE zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie die [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) -Methode auf, um die dem benutzerdefinierten Attribut zugeordneten Attribut Bytes zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
