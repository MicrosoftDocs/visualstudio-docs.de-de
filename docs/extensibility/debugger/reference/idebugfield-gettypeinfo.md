---
title: 'Idebugfield:: gettypeingefo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f74cc24d7698c3d83991c7f338bd2ef155ee1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869790"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Diese Methode ruft typunabhängige Informationen über das Symbol oder den Typ ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parameter
`pTypeInfo`\
vorgenommen Gibt Typinformationen in der angegebenen [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Typunabhängige Informationen sind z. b. die AppDomain, das Modul und die Klasse, die das Symbol enthält.

## <a name="see-also"></a>Weitere Informationen
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
