---
title: MSBuild-Inlineaufgaben | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild-Inlineaufgaben durch das Kompilieren einer Klasse erstellt werden können, die die Schnittstelle „Microsoft.Build.Framework.ITask“ implementiert.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 848e9c8c4e3dcc7d364f2001393730fbcc56be7e
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046333"
---
# <a name="msbuild-inline-tasks"></a>MSBuild-Inlineaufgaben

MSBuild-Aufgaben werden in der Regel durch Kompilieren einer Klasse erstellt, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).

 Ab .NET Framework Version 4 können Sie Aufgaben inline in der Projektdatei erstellen. Zum Hosten der Aufgabe müssen Sie keine separate Assembly erstellen. Dies vereinfacht das Nachverfolgen von Quellcode und das Bereitstellen der Aufgabe. Der Quellcode ist im Skript integriert.

 In MSBuild 15.8 wurde [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md) hinzugefügt, womit plattformübergreifende .NET Standard-Inlineaufgaben erstellt werden können.  Wenn Sie Inlineaufgaben in .NET Core verwenden müssen, müssen Sie RoslynCodeTaskFactory verwenden.
## <a name="the-structure-of-an-inline-task"></a>Struktur von Inlineaufgaben

 Inlineaufgaben sind in [UsingTask](../msbuild/usingtask-element-msbuild.md)-Elementen enthalten. Die Inlineaufgabe und das `UsingTask`-Element, in dem sie enthalten ist, befinden sich in der Regel in einer *TARGETS* -Datei und werden bei Bedarf in andere Projektdateien importiert. Im Folgenden finden Sie eine einfache Inlineaufgabe. Beachten Sie, dass mit dieser Aufgabe keine Aktionen ausgeführt werden.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
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

- Über das `AssemblyFile`-Attribut wird der Speicherort der Inlineaufgabenfactory angegeben. Sie können auch mit dem `AssemblyName`-Attribut den vollqualifizierten Namen der Inlineaufgabenfactory-Klasse angeben, die sich in der Regel in `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll` befindet.

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

## <a name="helloworld"></a>HelloWorld

 Im Folgenden finden Sie eine robustere Inlineaufgabe. Die HalloWelt-Aufgabe gibt „Hallo, Welt!“ auf dem Standardgerät für die Fehlerprotokollierung aus. In der Regel handelt es sich dabei um die Systemkonsole oder das Fenster **Ausgabe** in Visual Studio. Das `Reference`-Element im Beispiel wurde nur zur Veranschaulichung eingefügt.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
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

Wenn das `Code`-Element das `Type`-Attribut `Fragment` oder `Method` aufweist, werden für jeden Parameter automatisch Eigenschaften erstellt. Andernfalls müssen Eigenschaften explizit im Aufgabenquellcode deklariert werden und exakt mit den zugehörigen Parameterdefinitionen übereinstimmen.

## <a name="example"></a>Beispiel

 Mit der folgenden Inlineaufgabe wird jedes Vorkommen eines Tokens in der angegebenen Datei durch den angegebenen Wert ersetzt.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Exemplarische Vorgehensweise: Erstellen eines Inlinetasks](../msbuild/walkthrough-creating-an-inline-task.md)
