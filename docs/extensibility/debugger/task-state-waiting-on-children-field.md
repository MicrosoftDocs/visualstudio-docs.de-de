---
description: Der Task hat das Ausführen seines Delegaten abgeschlossen und wartet implizit auf den Abschluss angefügter untergeordneter Aufgaben.
title: TASK_STATE_WAITING_ON_CHILDREN Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1533ef28b32450d9b039c27e49ba655dddfd6ebe
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223203"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN Feld
Der Task hat das Ausführen seines Delegaten abgeschlossen und wartet implizit auf den Abschluss angefügter untergeordneter Aufgaben.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Bemerkungen
 Wenn das [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) -Feld diesen Wert enthält, <xref:System.Threading.Tasks.Task.Status%2A> gibt die-Eigenschaft zurück <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
