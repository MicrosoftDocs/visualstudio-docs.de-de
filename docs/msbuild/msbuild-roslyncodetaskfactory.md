---
title: MSBuild-Inlinetasks mit RoslynCodeTaskFactory | Microsoft-Dokumentation
description: Erfahren Sie mehr über die MSBuild-Aufgabe „RoslynCodeTaskFactory“, die den plattformübergreifenden Roslyn-Compiler verwendet, um In-Memory-Aufgabenassemblys für die Verwendung als Inlineaufgaben zu generieren.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c033c4d0ee36b9cb01618dd3ac3183e8782c70d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878421"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>MSBuild-Inlineaufgaben mit RoslynCodeTaskFactory

Ähnlich wie bei [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md) verwendet RoslynCodeTaskFactory die plattformübergeifenden Roslyn-Compiler, um In-Memory-Taskassemblys für die Verwendung als Inlinetasks zu generieren.  RoslynCodeTaskFactory-Tasks sind für .NET Standard vorgesehen und funktionieren ebenfalls mit .NET Framework- und .NET Core-Runtimes sowie auf anderen Plattformen wie Linux und macOS.

>[!NOTE]
>Der RoslynCodeTaskFactory-Task ist nur in MSBuild 15.8 und höher verfügbar. MSBuild-Versionen folgen den Versionen von Visual Studio. Daher ist RoslynCodeTaskFactory in Visual Studio 2017 ab Version 15.8 verfügbar.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Die Struktur einer Inlineaufgabe mit RoslynCodeTaskFactory

 RoslynCodeTaskFactory-Inlineaufgaben werden genau wie bei [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md) deklariert. Der einzige Unterschied liegt darin, dass Sie .NET Standard als Ziel verwenden.  Die Inlineaufgabe und das `UsingTask`-Element, in dem sie enthalten ist, befinden sich in der Regel in einer *TARGETS*-Datei und werden bei Bedarf in andere Projektdateien importiert. Im Folgenden finden Sie eine einfache Inlineaufgabe. Beachten Sie, dass mit dieser Aufgabe keine Aktionen ausgeführt werden.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 Das `UsingTask`-Element im Beispiel besitzt drei Attribute, die die Aufgabe und die Inlineaufgabenfactory beschreiben, die diese kompiliert.

- Die Aufgabe wird nach dem `TaskName`-Attribut benannt, in diesem Fall `DoNothing`.

- Nach dem `TaskFactory`-Attribut wird die Klasse benannt, die die Inlineaufgabenfactory implementiert.

- Über das `AssemblyFile`-Attribut wird der Speicherort der Inlineaufgabenfactory angegeben. Sie können auch mit dem `AssemblyName`-Attribut den vollqualifizierten Namen der Inlineaufgabenfactory-Klasse angeben, die sich in der Regel im globalen Assemblycache (Global Assembly Cache, GAC) befindet.

Die verbleibenden Elemente der `DoNothing`-Aufgabe sind leer und werden bereitgestellt, um die Reihenfolge und Struktur einer Inlineaufgabe zu veranschaulichen. Ein robusteres Beispiel wird weiter unten in diesem Thema präsentiert.

- Das `ParameterGroup`-Element ist optional. Bei Angabe werden die Parameter für die Aufgabe deklariert. Weitere Informationen zu Eingabe- und Ausgabeparametern finden Sie weiter unten in diesem Artikel unter [Eingabe- und Ausgabeparameter](#input-and-output-parameters).

- Das `Task`-Element beschreibt und enthält den Quellcode der Aufgabe.

- Das `Reference`-Element stellt Verweise auf die im Code verwendeten .NET-Assemblys bereit. Dies entspricht dem Hinzufügen eines Verweises auf ein Projekt in Visual Studio. Das `Include`-Attribut gibt den Pfad der Assembly an, auf die verwiesen wird.

- Das `Using`-Element führt die Namespaces auf, auf die Sie zugreifen möchten. Dies ähnelt der `Using`-Anweisung in Visual C#. Das `Namespace`-Attribut gibt den zu einschließenden Namespace an.

Das `Reference`-Element und das `Using`-Element sind sprachunabhängig. Inlineaufgaben können jeder unterstützten .NET CodeDom-Sprache geschrieben werden, z. B. Visual Basic oder Visual C#.

> [!NOTE]
> Elemente im `Task`-Element sind für die Aufgabenfactory spezifisch, in diesem Fall die Codeaufgabenfactory.

### <a name="code-element"></a>Codeelement

Als letztes untergeordnetes Element wird im `Task`-Element das `Code`-Element angegeben. Das `Code`-Element enthält oder sucht den Code, den Sie zu einer Aufgabe kompilieren möchten. Welche Elemente Sie im `Code`-Element einfügen, ist davon abhängig, wie Sie die Aufgabe erstellen möchten.

Das `Language`-Attribut gibt die Sprache an, in die der Code geschrieben ist. Zulässige Werte sind `cs` für C# und `vb` für Visual Basic.

Das `Type`-Attribut gibt den Typ von Code im `Code`-Element an.

- Wenn der Wert von `Type` auf `Class` festgelegt ist, enthält das `Code`-Element Code für eine Klasse, die von der <xref:Microsoft.Build.Framework.ITask>-Schnittstelle abgeleitet wird.

- Wenn der Wert von `Type` auf `Method` festgelegt ist, wird im Code die `Execute`-Methode der <xref:Microsoft.Build.Framework.ITask>-Schnittstelle überschrieben.

- Wenn der Wert von `Type` auf `Fragment` festgelegt ist, wird im Code der Inhalt der `Execute`-Methode, nicht jedoch die Signatur oder die `return`-Anweisung definiert.

Der Code selbst befindet sich in der Regel zwischen einem `<![CDATA[`-Marker und einem `]]>`-Marker. Da sich der Code in einem CDATA-Abschnitt befindet, müssen Sie reservierte Zeichen, z. B. \<" or ">, nicht mit Escapezeichen versehen.

Sie können den Speicherort einer Datei mit dem Code für die Aufgabe auch über das `Source`-Attribut des `Code`-Elements angeben. Der Code in der Quelldatei muss den vom `Type`-Attribut angegebenen Typ aufweisen. Bei vorhandenem `Source`-Attribut ist der Standardwert von `Type``Class`. Wenn `Source` nicht vorhanden ist, lautet der Standardwert `Fragment`.

> [!NOTE]
> Bei der Definition der Aufgabenklasse in der Quelldatei muss der Klassenname mit dem `TaskName`-Attribut des entsprechenden [UsingTask](../msbuild/usingtask-element-msbuild.md)-Elements übereinstimmen.

## <a name="hello-world"></a>Hello World

 Im Folgenden sehen Sie einen robusteren Inlinetask mit RoslynCodeTaskFactory: Die HalloWelt-Aufgabe gibt „Hallo, Welt!“ auf dem Standardgerät für die Fehlerprotokollierung aus. In der Regel handelt es sich dabei um die Systemkonsole oder das Fenster **Ausgabe** in Visual Studio. Das `Reference`-Element im Beispiel wurde nur zur Veranschaulichung eingefügt.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Sie können die HelloWorld-Aufgabe in der Datei *HelloWorld.targets* speichern und anschließend wie folgt in einem Projekt aufrufen.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Eingabe- und Ausgabeparameter

 Inlineaufgabenparameter bilden untergeordnete Elemente eines `ParameterGroup`-Elements. Jeder Parameter akzeptiert den Namen des Elements, das von ihm definiert wird. Im folgenden Code wird der Parameter `Text` definiert.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parameter können ein oder mehrere Attribute besitzen:

- `Required` ist ein optionales Attribut, das standardmäßig den Wert `false` besitzt. Bei `true` ist der Parameter erforderlich und muss vor dem Aufrufen der Aufgabe einen Wert erhalten.

- `ParameterType` ist ein optionales Attribut, das standardmäßig den Wert `System.String` besitzt. Es kann auf jeden vollqualifizierten Typ festgelegt werden, bei dem es sich um ein Element oder einen Wert handelt und mit System.Convert.ChangeType in und aus einer Zeichenfolge konvertiert werden kann. (Anders gesagt kann jeder Typ an eine und von einer externen Aufgabe übergeben werden.)

- `Output` ist ein optionales Attribut, das standardmäßig den Wert `false` besitzt. Bei `true` muss dem Parameter ein Wert zugewiesen werden, bevor die Execute-Methode die Rückgabe ausführt.

Ein auf ein Objekt angewendeter

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definiert die folgenden drei Parameter:

- `Expression` ist ein erforderlicher Eingabeparameter vom Typ System.String.

- `Files` ist ein erforderlicher Eingabeparameter für Elementlisten.

- `Tally` ist ein Ausgabeparameter vom Typ System.Int32.

Wenn das `Code`-Element das `Type`-Attribut `Fragment` oder `Method` aufweist, werden für jeden Parameter automatisch Eigenschaften erstellt.  Wenn in RoslynCodeTaskFactory das `Code`-Element über das `Type`-Attribut von `Class` verfügt, müssen Sie `ParameterGroup` nicht angeben, da es aus dem Quellcode abgeleitet wird (darin besteht ein Unterschied zu `CodeTaskFactory`). Andernfalls müssen Eigenschaften explizit im Aufgabenquellcode deklariert werden und exakt mit den zugehörigen Parameterdefinitionen übereinstimmen.

## <a name="example"></a>Beispiel

 Der folgende Inlinetask protokolliert einige Meldungen und gibt eine Zeichenfolge zurück.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Diese Inlinetasks können Pfade kombinieren und den Dateinamen abrufen.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Gewährleisten von Abwärtskompatibilität

`RoslynCodeTaskFactory` steht seit der MSBuild-Version 15.8 zur Verfügung. Angenommen, Sie haben eine Situation, in der Sie frühere Versionen von Visual Studio und MSBuild unterstützen möchten, bei der `RoslynCodeTaskFactory` im Gegensatz zu `CodeTaskFactory` nicht verfügbar war, Sie aber dasselbe Buildskript einsetzen möchten. Sie können ein `Choose`-Konstrukt verwenden, das die `$(MSBuildVersion)`-Eigenschaft verwendet, um zur Buildzeit zu entscheiden, ob die `RoslynCodeTaskFactory`-Eigenschaft verwendet oder auf `CodeTaskFactory` zurückgegriffen werden soll, wie im folgenden Beispiel:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Exemplarische Vorgehensweise: Erstellen eines Inlinetasks](../msbuild/walkthrough-creating-an-inline-task.md)
