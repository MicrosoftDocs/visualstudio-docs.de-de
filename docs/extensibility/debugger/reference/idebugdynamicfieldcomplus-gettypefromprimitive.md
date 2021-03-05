---
description: Ruft einen Typ ab, der den primitiven Typ erhält.
title: 'Idebugdynamicfieldcomplus:: gettypeer fromprimitive | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfd9b64a760a170791a921bb19508cfd6c789993
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167216"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Ruft einen Typ ab, der den primitiven Typ erhält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeFromPrimitive(
   DWORD         dwCorElementType,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromPrimitive(
   uint            dwCorElementType,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parameter
`dwCorElementType`\
in Der Wert aus der [CorElementType-Enumeration](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , der den primitiven Typ darstellt.

`ppType`\
vorgenommen Gibt das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Typ darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
