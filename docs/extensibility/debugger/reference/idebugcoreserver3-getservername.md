---
description: Ruft den Namen des Servers ab.
title: 'IDebugCoreServer3:: GetServerName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ee0bc7eeb97df19a06af5b9e02baebc73274be3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154703"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
Ruft den Namen des Servers ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
vorgenommen Gibt den Namen des Servers zurück.

> [!NOTE]
> Der Aufrufer ist für das Freigeben der Zeichenfolge verantwortlich.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn Sie einen benutzerfreundlichen Servernamen haben, müssen Sie die [getserverfriendlyname](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
