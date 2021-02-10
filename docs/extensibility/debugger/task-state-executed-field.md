---
title: TASK_STATE_EXECUTED Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 551ac7af1e331f9c1e57b078be4924994ebe8a3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968553"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED Feld
Die Aufgabe wird ausgeführt, wurde aber noch nicht abgeschlossen.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Bemerkungen
 Wenn das [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) -Feld diesen Wert enthält, <xref:System.Threading.Tasks.Task.Status%2A> gibt die-Eigenschaft zurück <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
