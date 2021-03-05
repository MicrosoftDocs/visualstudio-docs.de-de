---
description: Ruft einen anzeigen Amen für den Server ab.
title: 'IDebugCoreServer3:: getserverfriendlyname | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1ccb77cca920706dc7622e98dfca62743bf3b65
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163108"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Ruft einen anzeigen Amen für den Server ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
vorgenommen Gibt einen anzeigen Amen für den Server zurück.

> [!NOTE]
> Der Aufrufer ist für das Freigeben der Zeichenfolge verantwortlich.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Für vom Benutzer gestartete Server ist der Name, der von dieser Methode zurückgegeben wird, der vollständige Name des Servers. Für automatisch gestartete Server ist der Name der Name des Computers, auf dem der Server ausgeführt wird.

 Wenn Sie einen Computer orientierten Namen haben, müssen Sie die [getServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
