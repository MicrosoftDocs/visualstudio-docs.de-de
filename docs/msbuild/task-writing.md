---
title: Schreiben von Aufgaben | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eigene Aufgaben erstellen können, um den Code bereitzustellen, der während des MSBuild-Buildprozesses ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f13d561cba0482e15f065e66200b51c8b77ddfd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966018"
---
# <a name="task-writing"></a>Schreiben von Aufgaben

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Ziele enthalten Aufgaben. MSBuild umfasst eine Bibliothek mit typischen Aufgaben. Sie können aber auch Ihre eigenen Aufgaben erstellen. Weitere Informationen zu der in MSBuild enthaltenen Aufgabenbibliothek finden Sie in der [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Aufgaben

 Beispiele für Aufgaben sind u. a. [Copy](../msbuild/copy-task.md) zum Kopieren mindestens einer Datei, [MakeDir](../msbuild/makedir-task.md) zum Erstellen eines Verzeichnisses und [Csc](../msbuild/csc-task.md) zum Kompilieren einer C#-Quellcodedatei. Jede Aufgabe wird als .NET-Klasse implementiert, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert, die in der Assembly *Microsoft.Build.Framework.dll* definiert ist.

 Es gibt zwei Ansätze zur Implementierung einer Aufgabe:

- Implementieren Sie die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle direkt.

- Leiten Sie Ihre Klasse von der Hilfsklasse <xref:Microsoft.Build.Utilities.Task> ab, die in der Assembly *Microsoft.Build.Utilities.dll* definiert ist. „Task“ implementiert „ITask“ und stellt Standardimplementierungen einiger „ITask“-Elemente dar. Darüber hinaus wird die Protokollierung vereinfacht.

In beiden Fällen müssen Sie Ihrer Klasse eine Methode mit dem Namen `Execute` hinzufügen. Dabei handelt es sich um die Methode, die aufgerufen wird, wenn eine Aufgabe ausgeführt wird. Sie nimmt keine Parameter und gibt einen `Boolean`-Wert zurück: `true`, wenn die Aufgabe erfolgreich ausgeführt wurde oder `false`, wenn sie fehlgeschlagen ist. Im folgenden Beispiel wird eine Aufgabe dargestellt, die keine Aktion ausführt, aber `true` zurückgibt.

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Die folgende Projektdatei führt diese Aufgabe aus:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Wenn Aufgaben ausgeführt werden, können sie gleichzeitig Eingaben von der Projektdatei enthalten, wenn Sie .NET-Eigenschaften in der Aufgabenklasse erstellen. MSBuild legt diese Eigenschaften unmittelbar vor dem Aufrufen der `Execute`-Methode der Aufgabe fest. Verwenden Sie z.B. wie im Folgenden dargestellten Aufgabencode, um eine Zeichenfolgeneigenschaft zu erstellen:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Die folgende Projektdatei führt diese Aufgabe aus und legt `MyProperty` auf den vorhandenen Wert fest:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Protokollaufgaben

 Wenn das Projekt eine Aufgabe ausführen möchte, muss MSBuild wissen, wo die Assembly mit der Aufgabenklasse zu finden ist. Aufgaben werden über das [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md) registriert.

 Die MSBuild-Datei *Microsoft.Common.Tasks* ist eine Projektdatei mit einer Liste von `UsingTask`-Elementen, die alle Aufgaben registrieren, die mit MSBuild bereitgestellt werden. Diese Datei wird automatisch beim Erstellen von Projekten mit eingeschlossen. Wenn eine Aufgabe, die in *Microsoft.Common.Tasks* registriert wird, ebenfalls in der aktuellen Projektdatei registriert wird, hat die aktuelle Projektdatei Vorrang. Das heißt, Sie können eine Standardaufgabe mit Ihrer eigenen Aufgabe, die denselben Namen hat, außer Kraft setzen.

> [!TIP]
> Sie können eine Liste der mit MSBuild bereitgestellten Aufgaben anzeigen, indem Sie die Inhalte von *Microsoft.Common.Tasks* abrufen.

## <a name="raise-events-from-a-task"></a>Auslösen von Ereignissen aus einer Aufgabe

 Wenn Ihre Aufgabe aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitet wird, können Sie eine der folgenden Hilfsmethoden für die <xref:Microsoft.Build.Utilities.Task>-Klasse verwenden, damit ein Ereignis ausgelöst wird, das von allen registrierten Protokollierungen abgefangen und angezeigt wird:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Wenn Ihre Aufgabe <xref:Microsoft.Build.Framework.ITask> direkt implementiert, können Sie solche Ereignisse immer noch auslösen, allerdings nur noch über die IBuildEngine-Schnittstelle. Im folgenden Beispiel wird eine Aufgabe gezeigt, die „ITask“ implementiert und ein benutzerdefiniertes Ereignis auslöst:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Erfordern, dass Aufgabenparameter festgelegt werden

 Sie können Aufgabeneigenschaften als „Erforderlich“ markieren, damit jede Projektdatei, die die Aufgabe ausführt, Werte für diese Eigenschaften oder die fehlgeschlagenen Builds festlegt. Wenden Sie das erforderliche `[Required]`-Attribut in der .NET-Eigenschaft in Ihrer Aufgabe wie folgt an:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Das `[Required]`-Attribut wird von <xref:Microsoft.Build.Framework.RequiredAttribute> im <xref:Microsoft.Build.Framework>-Namespace definiert.

## <a name="how-msbuild-invokes-a-task"></a>Aufruf einer Aufgabe durch MSBuild

Zum Aufrufen einer Aufgabe instanziiert MSBuild zunächst die Aufgabenklasse. Anschließend werden die Eigenschaftensetter des Objekts für Aufgabenparameter aufgerufen, die in der Projektdatei im Aufgabenelement festgelegt sind. Der Eigenschaftensetter wird nicht aufgerufen, wenn das Aufgabenelement keinen Parameter angibt oder der im Element angegebene Ausdruck eine leere Zeichenfolge ergibt.

Sehen Sie sich z. B. folgendes Projekt an:

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

Hier wird nur der Setter für `Input3` aufgerufen.

Eine Aufgabe sollte nicht von der relativen Reihenfolge des Aufrufs von Parameter und Eigenschaftensetter abhängen.

### <a name="task-parameter-types"></a>Typen von Aufgabenparametern

In MSBuild erfolgt werden die Eigenschaften vom Typ `string`, `bool`, `ITaskItem` und `ITaskItem[]` nativ verarbeitet. Akzeptiert eine Aufgabe einen Parameter eines anderen Typs, ruft MSBuild <xref:System.Convert.ChangeType%2A> auf, um eine Konvertierung von `string` (mit Erweiterung aller Eigenschaften- und Elementverweise) in den Zieltyp durchzuführen. Ist die Konvertierung für einen Eingabeparameter nicht erfolgreich, gibt MSBuild einen Fehler aus und ruft die Methode `Execute()` der Aufgabe nicht auf.

## <a name="example-1"></a>Beispiel 1

### <a name="description"></a>Beschreibung

Die folgende C#-Klasse veranschaulicht eine aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitete Aufgabe. Dieser Task gibt den Wert `true` zurück, der darauf hindeutet, dass der Task erfolgreich ausgeführt wird.

### <a name="code"></a>Code

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Beispiel 2

### <a name="description"></a>Beschreibung

Die folgende C#-Klasse veranschaulicht eine Aufgabe zur Implementierung der <xref:Microsoft.Build.Framework.ITask>-Schnittstelle. Dieser Task gibt den Wert `true` zurück, der darauf hindeutet, dass der Task erfolgreich ausgeführt wird.

### <a name="code"></a>Code

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Beispiel 3

### <a name="description"></a>Beschreibung

Diese C#-Klasse veranschaulicht eine aus der <xref:Microsoft.Build.Utilities.Task>-Hilfsklasse abgeleitete Aufgabe. Sie verfügt über eine erforderliche Zeichenfolgeneigenschaft und löst ein Ereignis aus, das von allen registrierten Protokollierungen angezeigt wird.

### <a name="code"></a>Code

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example-4"></a>Beispiel 4

### <a name="description"></a>Beschreibung

Im folgenden Beispiel wird eine Projektdatei dargestellt, die die vorherigen Beispielaufgabe „SimpleTask3“ aufruft.

### <a name="code"></a>Code

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
