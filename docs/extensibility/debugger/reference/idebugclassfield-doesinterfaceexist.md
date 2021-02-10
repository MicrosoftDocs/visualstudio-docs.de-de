---
title: Idebugclassfield::D oesinterfaceexist | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7116b9e675605863805fb413340ea8b45ec608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947111"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parameter
`pszInterfaceName`\
in Eine Zeichenfolge mit dem Schnittstellennamen, nach dem gesucht werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. gibt S_FALSE zurück, wenn die Schnittstelle nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ruft in der Regel eine Enumeration aller Schnittstellen ab und durchsucht die Liste nach einer entsprechenden Schnittstelle.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
