---
title: 'Vorgehensweise: Konfigurieren von Zielen und Aufgaben | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ausgewählte MSBuild-Aufgaben unabhängig von der Umgebung des Entwicklungscomputers zur Ausführung in der Umgebung festlegen, für die sie bestimmt sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31537ea44e5c49a4fd98229a5886ca99a1464409
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435770"
---
# <a name="how-to-configure-targets-and-tasks"></a>Vorgehensweise: Konfigurieren von Zielen und Aufgaben

Ausgewählte MSBuild-Aufgaben können unabhängig von der Umgebung des Entwicklungscomputers zur Ausführung in der Umgebung, für die sie bestimmt sind, eingestellt werden. Wenn Sie z.B. einen 64-Bit-Computer zum Erstellen einer Anwendung verwenden, die in einer 32-Bit-Architektur ausgeführt werden soll, werden ausgewählte Vorgänge in einem 32-Bit-Prozess ausgeführt.
Ausgewählte MSBuild-Aufgaben können unabhängig von der Umgebung des Entwicklungscomputers zur Ausführung in der Umgebung, für die sie bestimmt sind, eingestellt werden. Wenn Sie z.B. einen 64-Bit-Computer zum Erstellen einer Anwendung verwenden, die in einer 32-Bit-Architektur ausgeführt werden soll, werden ausgewählte Vorgänge in einem 32-Bit-Prozess ausgeführt.

> [!NOTE]
> Wenn eine Buildaufgabe in einer .NET-Sprache wie z.B. Visual C# oder Visual Basic geschrieben ist und keine nativen Ressourcen oder Tools verwendet, wird sie in jedem Zielkontext ohne Anpassung ausgeführt.

## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask-Attribute und Aufgabenparameter

Die folgenden `UsingTask`-Attribute wirken sich auf alle Vorgänge einer Aufgabe in einem bestimmten Buildprozess aus:

- Das `Runtime`-Attribut, sofern vorhanden, legt die Version der Common Language Runtime (CLR) fest, und kann einen der folgenden Werte annehmen: `CLR2`, `CLR4`, `CurrentRuntime` oder `*` (beliebige Runtime).

- Das `Architecture`-Attribut, sofern vorhanden, legt Plattform und Bitanzahl fest und kann einen der folgenden Werte annehmen: `x86`, `x64`, `CurrentArchitecture` oder `*` (beliebige Architektur).

- Das `TaskFactory`-Attribut, sofern vorhanden, legt die Aufgabenfactory fest, die die Aufgabeninstanz erstellt und ausführt, und nimmt nur den Wert `TaskHostFactory` an. Weitere Informationen finden Sie im Abschnitt [Aufgabenfactorys](#task-factories) weiter unten in diesem Artikel.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Sie können auch mit den Parametern `MSBuildRuntime` und `MSBuildArchitecture` den Zielkontext einer einzelnen Aufgabe festlegen.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Bevor MSBuild eine Aufgabe ausführt, wird nach einer übereinstimmenden `UsingTask` mit gleichem Zielkontext gesucht. In der `UsingTask`, jedoch nicht in der entsprechenden Aufgabe angegebene Parameter werden als übereinstimmend betrachtet. In der Aufgabe, jedoch nicht in der entsprechenden `UsingTask` angegebene Parameter werden auch als übereinstimmend betrachtet. Wenn Parameterwerte weder in der `UsingTask` noch in der Aufgabe angegeben sind, sind die Werte standardmäßig `*` (beliebiger Parameter).

> [!WARNING]
> Wenn mehr als eine `UsingTask` vorhanden ist und alle übereinstimmende `TaskName`-, `Runtime`- und `Architecture`-Attribute haben, ersetzt die zuletzt ausgewertete die anderen.

 Wenn Parameter für die Aufgabe festgelegt sind, versucht MSBuild, eine `UsingTask` zu finden, die mit diesen Parametern übereinstimmt oder zumindest nicht in Konflikt mit ihnen steht. Mehr als eine `UsingTask` können den Zielkontext der gleichen Aufgabe angeben. Beispielsweise könnte eine Aufgabe mit verschiedenen ausführbaren Dateien für unterschiedliche Zielumgebungen dieser ähneln:

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>Aufgabenfactorys

Bevor eine Aufgabe ausgeführt wird, überprüft MSBuild, ob sie zur Ausführung im aktuellen Softwarekontext bestimmt ist. Wenn die Aufgabe hierfür bestimmt ist, übergibt MSBuild sie an die AssemblyTaskFactory, die sie im aktuellen Prozess ausführt; andernfalls übergibt MSBuild die Aufgabe an die TaskHostFactory, die die Aufgabe in einem Prozess ausführt, der dem Zielkontext entspricht. Auch wenn aktueller Kontext und Zielkontext übereinstimmen, können Sie durch Festlegen von `TaskFactory` auf `TaskHostFactory` erzwingen, dass eine Aufgabe prozessextern ausgeführt wird (zur Isolation, zur Sicherheit oder aus anderen Gründen).

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Phantomaufgabenparameter

Wie alle anderen Aufgabenparameter können `MSBuildRuntime` und `MSBuildArchitecture` über die Buildeigenschaften festgelegt werden .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Im Gegensatz zu anderen Aufgabenparametern sind `MSBuildRuntime` und `MSBuildArchitecture` für die Aufgabe selbst nicht ersichtlich. Um eine Aufgabe zu schreiben, die sich des Kontexts bewusst ist, in dem sie ausgeführt wird, müssen Sie entweder den Kontext durch Aufrufen von .NET Framework testen oder Buildeigenschaften verwenden, um die Kontextinformationen über andere Aufgabenparameter zu übergeben.

> [!NOTE]
> `UsingTask`-Attribute können aus Toolset und Umgebungseigenschaften festgelegt werden.

Die Parameter `MSBuildRuntime` und `MSBuildArchitecture` bieten die flexibelste Möglichkeit, um den Zielkontext festzulegen, zugleich ist der Umfang aber am stärksten begrenzt. Einerseits können sie ihren Wert aus dem vollen Umfang an Eigenschaften ableiten, die zur Auswertungs- und Buildzeit verfügbar sind, da sie auf der Aufgabeninstanz selbst festgelegt werden und nicht ausgewertet werden, bis die Aufgabe ausgeführt wird. Andererseits gelten diese Parameter nur für eine bestimmte Instanz einer Aufgabe in einem bestimmten Ziel.

> [!NOTE]
> Aufgabenparameter werden im Kontext des übergeordneten Knotens ausgewertet, nicht im Kontext des Aufgabenhosts. Umgebungsvariablen, die von der Laufzeit oder Architektur abhängen (wie der Speicherort der *Programme* ) ergeben bei der Auswertung den Wert, der dem übergeordneten Knoten entspricht. Wenn dieselbe Umgebungsvariable jedoch direkt von der Aufgabe gelesen wird, wird sie ordnungsgemäß im Kontext des Aufgabenhosts ausgewertet.

## <a name="see-also"></a>Siehe auch

- [Konfigurieren von Zielen und Aufgaben](../msbuild/configuring-targets-and-tasks.md)
- [UsingTask-Element](../msbuild/usingtask-element-msbuild.md)
