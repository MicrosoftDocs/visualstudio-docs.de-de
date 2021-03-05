---
description: Hiermit wird eine ausführbare Datei gestartet.
title: 'IDebugPortEx2:: launchangeh alten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5982ad665333aa4d11e2098d3b148db88e77c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142823"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Hiermit wird eine ausführbare Datei gestartet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parameter
`pszExe`\
in Der Name der ausführbaren Datei, die gestartet werden soll. Dies kann ein vollständiger Pfad oder relativ zum Arbeitsverzeichnis sein, das im-Parameter angegeben ist `pszDir` .

`pszArgs`\
in Die an die ausführbare Datei zu über gebenden Argumente. Kann ein NULL-Wert sein, wenn keine Argumente vorhanden sind.

`pszDir`\
in Der Name des Arbeitsverzeichnisses, das von der ausführbaren Datei verwendet wird. Kann ein NULL-Wert sein, wenn kein Arbeitsverzeichnis erforderlich ist.

`bstrEnv`\
in Umgebungsblock mit null-terminierten Zeichen folgen, gefolgt von einem zusätzlichen null-Terminator.

`hStdInput`\
in Handle für einen alternativen Eingabedaten Strom. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`hStdOutput`\
in Handle für einen alternativen Ausgabestream. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`hStdError`\
in Handle für einen alternativen Fehlerausgabestream. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`ppPortProcess`\
vorgenommen Gibt ein [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt zurück, das den gestarteten Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode sollte den Prozess starten, sodass er angehalten und keinen Code ausgeführt wird. Die [resumeprocess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) -Methode wird aufgerufen, um den Prozess fortzusetzen.

 Ein Programm kann auch über eine Debug-Engine gestartet werden. Weitere Informationen finden Sie unter [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md)
