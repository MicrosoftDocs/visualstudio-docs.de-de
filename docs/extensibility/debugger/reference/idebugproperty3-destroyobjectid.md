---
description: Zerstört die eindeutige ID, die dieser Eigenschaft zugeordnet ist, und gibt an, dass der Aufrufer nicht mehr interessiert ist, diese Eigenschaft eindeutig aus allen anderen Eigenschaften zu identifizieren.
title: IDebugProperty3::D estroyobjectid | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3712a12440f5d177f54544110bc8fa5d2e03ac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166696"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Zerstört die eindeutige ID, die dieser Eigenschaft zugeordnet ist, und gibt an, dass der Aufrufer nicht mehr interessiert ist, diese Eigenschaft eindeutig aus allen anderen Eigenschaften zu identifizieren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn die Debug-Engine eindeutige IDs für eine Eigenschaft nicht unterstützen muss (weil Sie diese bereits eindeutig nachverfolgt), kann Sie einfach `E_NOTIMPL` für diese Methode zurückgeben.

 Eindeutige IDs werden mit einem Aufruf der Methode " [kreateobjectid](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) " erstellt, wenn der Aufrufer sicherstellen möchte, dass diese Eigenschaft unter allen anderen Eigenschaften eindeutig identifiziert wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
