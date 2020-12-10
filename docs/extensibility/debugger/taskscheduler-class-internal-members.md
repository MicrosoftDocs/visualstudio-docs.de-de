---
title: 'TaskScheduler-Klasse: interne Member | Microsoft-Dokumentation'
description: Erfahren Sie mehr über die internen Member der System. Threading. Tasks. TaskScheduler-Klasse, die Sie bei der Implementierung eines benutzerdefinierten Debuggers unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10528e57137f8605e7f140d4ab8d4a3399029a5f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996005"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler-Klasse: interne Member
In diesem Artikel werden die internen Member der- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse beschrieben, die Ihnen bei der Implementierung eines benutzerdefinierten Debuggers helfen. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Threading.Tasks.TaskScheduler> Referenz Artikel.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Ruft ein Array aller geplanten Tasks ab.|
|[Gettaskschedulersfordebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Ruft ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte ab, die derzeit aktiv sind.|

## <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
