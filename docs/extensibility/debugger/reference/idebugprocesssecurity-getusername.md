---
description: Ruft den Benutzernamen vom Port Lieferanten ab.
title: 'Idebugprocesssecurity:: GetUserName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166202"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ruft den Benutzernamen vom Port Lieferanten ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parameter
`pbstrUserName`\
vorgenommen Eine Zeichenfolge, die den Benutzernamen enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 `GetUserName` Gibt den Benutzernamen zurück, der in der Spalte **Benutzername** im Dialogfeld **an den Prozess anhängen** angezeigt wird. Um das Dialogfeld **an den Prozess anhängen** anzuzeigen, klicken Sie **im Menü Extras in der** integrierten Entwicklungsumgebung (IDE) auf **an den Prozess anhängen** [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
