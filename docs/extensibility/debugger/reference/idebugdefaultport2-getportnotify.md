---
description: Diese Methode ruft eine IDebugPortNotify2-Schnittstelle für diesen Port ab.
title: 'IDebugDefaultPort2:: getportnotify | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd0d49275188eed1cebb7b1af3ee4dfcbb79cbe4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150652"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Diese Methode ruft eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Schnittstelle für diesen Port ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parameter
`ppPortNotify`\
vorgenommen Ein [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Normalerweise wird die- `QueryInterface` Methode für das Objekt aufgerufen, das die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle implementiert, um eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Schnittstelle abzurufen. Es gibt jedoch Situationen, in denen die gewünschte Schnittstelle auf einem anderen Objekt implementiert wird. Diese Methode verbirgt diese Umstände und gibt die- `IDebugPortNotify2` Schnittstelle aus dem am besten geeigneten-Objekt zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
