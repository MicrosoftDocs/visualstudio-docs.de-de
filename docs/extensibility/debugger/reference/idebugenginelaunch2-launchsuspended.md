---
description: Mit dieser Methode wird ein Prozess mithilfe der Debug-Engine (de) gestartet.
title: 'IDebugEngineLaunch2:: launchangeh alten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9fd8b610f99161a9716b9bffc235196165306711
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153585"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Mit dieser Methode wird ein Prozess mithilfe der Debug-Engine (de) gestartet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parameter
`pszMachine`\
in Der Name des Computers, auf dem der Prozess gestartet werden soll. Verwenden Sie einen NULL-Wert, um den lokalen Computer anzugeben.

`pPort`\
in Die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die den Port darstellt, in dem das Programm ausgeführt wird.

`pszExe`\
in Der Name der ausführbaren Datei, die gestartet werden soll.

`pszArgs`\
in Die an die ausführbare Datei zu über gebenden Argumente. Kann ein NULL-Wert sein, wenn keine Argumente vorhanden sind.

`pszDir`\
in Der Name des Arbeitsverzeichnisses, das von der ausführbaren Datei verwendet wird. Kann ein NULL-Wert sein, wenn kein Arbeitsverzeichnis erforderlich ist.

`bstrEnv`\
in Umgebungsblock mit null-terminierten Zeichen folgen, gefolgt von einem zusätzlichen null-Terminator.

`pszOptions`\
in Die Optionen für die ausführbare Datei.

`dwLaunchFlags`\
in Gibt die [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) für eine Sitzung an.

`hStdInput`\
in Handle für einen alternativen Eingabedaten Strom. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`hStdOutput`\
in Handle für einen alternativen Ausgabestream. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`hStdError`\
in Handle für einen alternativen Fehlerausgabestream. Kann 0 sein, wenn eine Umleitung nicht erforderlich ist.

`pCallback`\
in Das [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das Debugger-Ereignisse empfängt.

`ppDebugProcess`\
vorgenommen Gibt das resultierende [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt zurück, das den gestarteten Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Normalerweise wird [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ein Programm mit der [launchangeh](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) alten-Methode gestartet und dann der Debugger an das angehaltene Programm angefügt. Es gibt jedoch Situationen, in denen die Debug-Engine möglicherweise ein Programm starten muss (z. b. wenn die Debug-Engine Teil eines interpreters ist und das zu debuggende Programm eine interpretierte Sprache ist). in diesem Fall wird [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] die- `IDebugEngineLaunch2::LaunchSuspended` Methode verwendet.

 Die [resumeprocess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) -Methode wird aufgerufen, um den Prozess zu starten, nachdem der Prozess erfolgreich im angehaltenen Zustand gestartet wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
