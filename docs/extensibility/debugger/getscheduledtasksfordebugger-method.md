---
description: Ruft ein Array aller geplanten Tasks ab.
title: GetScheduledTasksForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd70db6f6fd9eb1558a21e50f3d2f63137fe8e1d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167814"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
Ruft ein Array aller geplanten Tasks ab.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller geplanten Tasks. Jede Aufgabe wird ausgeführt oder die Ausführung ist abgeschlossen.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Thread sicher und sollte nicht gleichzeitig mit anderen Instanzen von verwendet werden <xref:System.Threading.Tasks.TaskScheduler> . Diese Methode wird nur von einem Debugger aufgerufen, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Weitere Informationen
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
