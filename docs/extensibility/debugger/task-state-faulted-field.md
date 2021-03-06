---
description: Die Aufgabe wurde aufgrund eines Ausnahmefehlers abgeschlossen.
title: TASK_STATE_FAULTED Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5a8113f6145706d2863a4f0060a8627952eb0b3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223185"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED Feld
Die Aufgabe wurde aufgrund eines Ausnahmefehlers abgeschlossen.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Bemerkungen
 Wenn das [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) -Feld diesen Wert enthält, <xref:System.Threading.Tasks.Task.Status%2A> gibt die-Eigenschaft zurück <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
