---
title: Aufgaben Klasse-interne Member | Microsoft-Dokumentation
description: Erfahren Sie mehr über die internen Member der System. Threading. Tasks. Task-Klasse, die Sie bei der Implementierung eines benutzerdefinierten Debuggers unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f18de66a524fbc652b8153c5b34b4464cda60f5
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996018"
---
# <a name="task-class---internal-members"></a>Aufgaben Klasse-interne Member
In diesem Artikel werden die internen Member der- <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse beschrieben, die Ihnen bei der Implementierung eines benutzerdefinierten Debuggers helfen. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Threading.Tasks.Task> Referenz Artikel.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[SetNotificationForWaitCompletion-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Legt das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustands Bit fest oder löscht dieses.|
|[NotifyDebuggerOfWaitCompletion-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Die Platzhalter Methode, die vom Debugger als Haltepunkt Ziel verwendet wird.|

### <a name="fields"></a>Felder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den Code darstellt, der im-Objekt ausgeführt werden soll <xref:System.Threading.Tasks.Task> .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften des- <xref:System.Threading.Tasks.Task> Objekts.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Das Unterstützungs Feld für die über <xref:System.Threading.Tasks.Task?displayProperty=fullName> geordnete Eigenschaft.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen zum aktuellen Zustand des <xref:System.Threading.Tasks.Task> Objekts.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein-Objekt, das Daten darstellt, die von der Aktion verwendet werden.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Das Unterstützungs Feld für die- <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Eigenschaft.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Der nächste verfügbare Bezeichner für ein- <xref:System.Threading.Tasks.Task> Objekt.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass der Task abgebrochen wurde, bevor er den Ausführungs Zustand erreicht hat, oder dass der Task seinen Abbruch bestätigt und ohne Ausnahme abgeschlossen hat.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass der Task aufgrund einer nicht behandelten Ausnahme abgeschlossen wurde.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass die Ausführung der Aufgabe erfolgreich abgeschlossen wurde.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass der Task die Ausführung seines Delegaten beendet hat, und wartet implizit auf den Abschluss angefügter untergeordneter Aufgaben.|

## <a name="remarks"></a>Bemerkungen
 Die folgenden internen Methoden sind für eine Debugger-Engine nützlich, da Sie den Eingang zur <xref:System.Threading.Tasks.Task> Codeausführung markieren:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
