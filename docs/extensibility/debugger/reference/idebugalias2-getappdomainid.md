---
description: Ruft den Bezeichner für die Anwendungsdomäne ab.
title: 'IDebugAlias2:: getappdomainid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f5bd0d6a96ad41409b87433599fe693fc86c1cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143869"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Ruft den Bezeichner für die Anwendungsdomäne ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parameter
`pappDomainId`\
vorgenommen Gibt den Bezeichner der Anwendungsdomäne zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Bezeichner der Anwendungsdomäne wird immer dann geändert, wenn die Anwendung neu gestartet und eine neue Anwendungsdomäne erstellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
