---
description: Ruft ein Array aller System. Threading. Tasks. TaskScheduler-Objekte ab, die derzeit aktiv sind.
title: Gettaskschedulersfordebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f60ffa851e8b8821e3d07e1bfdd6e864104b5001
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150093"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger-Methode
Ruft ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte ab, die derzeit aktiv sind.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit in diesem aktiv sind <xref:System.AppDomain> .

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Thread sicher und sollte nicht gleichzeitig mit anderen Instanzen von verwendet werden <xref:System.Threading.Tasks.TaskScheduler> . Diese Methode wird nur von einem Debugger aufgerufen, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Weitere Informationen
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
