---
title: IDebugCoreServer3::D iagno-webdebug Fehler Error | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6c95c3953b70235daa739e48b5de50b4a815b13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908055"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Versucht zu bestimmen, warum ein Automatisches Anfügen fehlgeschlagen ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parameter
`pszUrl`\
in Derzeit nicht verwendet; sollte immer auf einen NULL-Wert festgelegt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Im folgenden sind andere typische Rückgabecodes aufgeführt:

|Code|BESCHREIBUNG|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Es kann nicht bestimmt werden, warum der Remote Server das Debugging nicht starten konnte.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Kann nicht auf einem Remote Server debuggt werden, möglicherweise aufgrund unzureichender Berechtigungen oder weil das DEBUG-Verb nicht aktiviert ist.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Der Webserver wurde gesperrt und blockiert das DEBUG-Verb, das zum Aktivieren des Debuggens erforderlich ist.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
