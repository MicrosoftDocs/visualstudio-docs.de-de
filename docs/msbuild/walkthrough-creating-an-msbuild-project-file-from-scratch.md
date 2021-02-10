---
title: Erstellen einer neuen MSBuild-Projektdatei
description: Exemplarische Vorgehensweise zum Erstellen einer MSBuild-Projektdatei von Grund auf, um die XML-Struktur kennenzulernen und zu verstehen, wie deren Änderung zur Steuerung eines Builds genutzt werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3d0462382ddcc86a23c7e25162fb429b9f9893
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967539"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei

Programmiersprachen für das .NET Framework verwenden MSBuild-Projektdateien zum Beschreiben und Steuern des Anwendungsbuildprozesses. Wenn Sie in Visual Studio eine MSBuild-Projektdatei erstellen, wird der Datei automatisch das entsprechende XML hinzugefügt. Ein Grundverständnis der Organisation des XML und der Änderungsmöglichkeiten zum Steuern eines Builds ist jedoch empfehlenswert.

 Weitere Informationen zum Erstellen einer Projektdatei für ein C++-Projekt finden Sie unter [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 In dieser exemplarischen Vorgehensweise wird das inkrementelle Erstellen einer einfachen Projektdatei nur mit einem Texteditor veranschaulicht. In der exemplarischen Vorgehensweise werden die nachfolgenden Schritte ausgeführt:

1. Erweitern Sie die PATH-Umgebungsvariable.

2. Erstellen einer minimalen Anwendungsquelldatei

3. Erstellen einer minimalen MSBuild-Projektdatei

4. Erstellen der Anwendung mit der Projektdatei

5. Hinzufügen von Eigenschaften zum Steuern des Builds

6. Steuern des Builds durch Ändern von Eigenschaftswerten

7. Hinzufügen von Zielen zum Build

8. Steuern des Build durch Hinzufügen von Zielen

9. Inkrementeller Build

In dieser exemplarischen Vorgehensweise werden das Erstellen des Projekts an der Eingabeaufforderung und das Untersuchen der Ergebnisse veranschaulicht. Weitere Informationen zu MSBuild und zum Ausführen von MSBuild an der Eingabeaufforderung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md).

Sie können die exemplarische Vorgehensweise nur ausführen, wenn Sie Visual Studio installiert haben, da darin MSBuild und der Visual C#-Compiler enthalten sind, die für die exemplarische Vorgehensweise erforderlich sind.

## <a name="extend-the-path"></a>Erweitern des Pfads

Bevor Sie MSBuild verwenden können, müssen Sie die PATH-Umgebungsvariable so erweitern, dass Sie alle erforderlichen Tools enthält. Sie können die **Developer-Eingabeaufforderung für Visual Studio** verwenden. Suchen Sie unter Windows 10 im Suchfeld auf der Windows-Taskleiste danach. Wenn Sie die Umgebung in einer gewöhnlichen Eingabeaufforderung oder in einer Skriptumgebung einrichten möchten, führen Sie *VSDevCmd.bat* im Unterordner *Common7/Tools* einer Visual Studio-Installation aus.

## <a name="create-a-minimal-application"></a>Erstellen einer minimalen Anwendung

 In diesem Abschnitt wird veranschaulicht, wie Sie eine minimale Visual C#-Anwendungsquelldatei mithilfe eines Text-Editors erstellen.

1. Wechseln Sie an der Eingabeaufforderung zu dem Ordner, in dem Sie die Anwendung erstellen möchten, z.B. *\Eigene Dateien\\* oder *\Desktop\\* .

2. Geben Sie **md HelloWorld** ein, um den Unterordner *\HelloWorld\\* zu erstellen.

3. Geben Sie **cd HelloWorld** ein, um zum neuen Ordner zu wechseln.

4. Starten Sie Editor oder einen anderen Texteditor, und geben Sie dann den folgenden Code ein.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Speichern Sie diese Quellcodedatei, und nennen Sie sie *Helloworld.cs*.

6. Erstellen Sie die Anwendung, indem Sie an der Eingabeaufforderung **csc helloworld.cs** eingeben.

7. Testen Sie die Anwendung, indem Sie an der Eingabeaufforderung **helloworld** eingeben.

     Die Meldung **Hello, world!** sollte angezeigt werden.

8. Löschen Sie die Anwendung, indem Sie an der Eingabeaufforderung **del helloworld.exe** eingeben.

## <a name="create-a-minimal-msbuild-project-file"></a>Erstellen einer minimalen MSBuild-Projektdatei

 Da Sie nun über eine minimale Anwendungsquelldatei verfügen, können Sie eine minimale Projektdatei für den Build der Anwendung erstellen. Diese Projektdatei enthält die folgenden Elemente:

- Erforderlicher `Project`-Stammknoten

- `ItemGroup`-Knoten mit Elementelementen

- Elementelement, das auf die Anwendungsquelldatei verweist

- `Target`-Knoten mit Aufgaben, die für den Build der Anwendung erforderlich sind.

- Ein `Task`-Element, mit dem der Visual C#-Compiler für den Build der Anwendung gestartet wird.

### <a name="to-create-a-minimal-msbuild-project-file"></a>So erstellen Sie eine minimale MSBuild-Projektdatei

1. Ersetzen Sie im Texteditor den vorhandenen Text durch die beiden folgenden Zeilen:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Fügen Sie diesen `ItemGroup`-Knoten als untergeordnetes Element des `Project`-Knotens ein:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Beachten Sie, dass diese `ItemGroup` bereits ein Elementelement enthält.

3. Fügen Sie einen `Target`-Knoten als untergeordnetes Element des `Project`-Knotens ein. Benennen Sie den Knoten mit `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Fügen Sie dieses Aufgabenelement als untergeordnetes Element des `Target`-Knotens ein:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Speichern Sie diese Projektdatei, und nennen Sie sie *Helloworld.csproj*.

Die minimale Projektdatei sollte dem folgenden Code ähneln:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Aufgaben im Build-Ziel werden sequenziell ausgeführt. In diesem Fall bildet die `Csc`-Aufgabe des Visual C#-Compilers die einzige Aufgabe. Erwartet wird eine Liste zu kompilierender Quelldateien, angegeben durch den Wert des `Compile`-Elements. Das `Compile`-Element verweist nur auf eine einzelne Quelldatei, *Helloworld.cs*.

> [!NOTE]
> Im Elementelement können Sie wie folgt mithilfe des Platzhalterzeichens Sternchen (\*) auf alle Dateien mit der Dateinamenerweiterung *CS* verweisen:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Erstellen der Anwendung

 Für den Build der Anwendung verwenden Sie nun die Projektdatei, die Sie eben erstellt haben.

1. Geben Sie an der Eingabeaufforderung **msbuild helloworld.csproj -t:Build** ein.

     Damit wird das Build-Ziel der Helloworld-Projektdatei erstellt, da der Visual C#-Compiler aufgerufen wird, um die Anwendung Helloworld zu erstellen.

2. Testen Sie die Anwendung, indem Sie **helloworld** eingeben.

     Die Meldung **Hello, world!** sollte angezeigt werden.

> [!NOTE]
> Weitere Details zum Build werden angezeigt, wenn Sie den Ausführlichkeitsgrad erhöhen. Um den Ausführlichkeitsgrad auf „Detailliert“ festzulegen, geben Sie diesen Befehl an der Eingabeaufforderung ein:
>
> **msbuild helloworld.csproj -t:Build -verbosity:detailed**

## <a name="add-build-properties"></a>Hinzufügen der Buildeigenschaften

 Sie können der Projektdatei Buildeigenschaften hinzufügen, um den Build genauer steuern zu können. Fügen Sie jetzt die folgenden Eigenschaften hinzu:

- Eine `AssemblyName`-Eigenschaft, mit der der Name der Anwendung angegeben wird

- Eine `OutputPath`-Eigenschaft, mit der ein Ordner für die Anwendung angegeben wird

### <a name="to-add-build-properties"></a>So fügen Sie Buildeigenschaften hinzu

1. Löschen Sie die vorhandene Anwendung, indem Sie an der Eingabeaufforderung **del helloworld.exe** eingeben.

2. Fügen Sie in der Projektdatei nach dem ersten `PropertyGroup`-Element das folgende `Project`-Element ein:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Fügen Sie dem Build-Ziel direkt vor der `Csc`-Aufgabe die folgende Aufgabe hinzu:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Mit der `MakeDir`-Aufgabe wird ein Ordner erstellt, der nach der `OutputPath`-Eigenschaft benannt wird, sofern noch kein Ordner mit diesem Namen vorhanden ist.

4. Fügen Sie der `OutputAssembly`-Aufgabe das folgende `Csc`-Attribut hinzu:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Damit wird der Visual C#-Compiler angewiesen, eine nach der `AssemblyName`-Eigenschaft benannte Assembly zu erzeugen und diese in dem nach der `OutputPath`-Eigenschaft benannten Ordner einzufügen.

5. Speichern Sie die Änderungen.

Die Projektdatei sollte nun dem folgenden Code ähneln:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> Es wird empfohlen, den umgekehrten Schrägstrich (\\) als Pfadtrennzeichen am Ende des Ordnernamens bei der Angabe im Element `OutputPath` anzufügen und nicht im Attribut `OutputAssembly` der Aufgabe `Csc`. Daher eignet sich
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> besser als
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testen der Buildeigenschaften

 Nun können Sie die Anwendung mithilfe der Projektdatei erstellen, in der Sie über Buildeigenschaften den Ausgabeordner und den Anwendungsnamen angegeben haben.

1. Geben Sie an der Eingabeaufforderung **msbuild helloworld.csproj -t:Build** ein.

     Damit wird der Ordner *\Bin\\* erstellt und anschließend der Visual C#-Compiler aufgerufen, um die Anwendung *MSBuildSample* zu erstellen und im Ordner *\Bin\\* einzufügen.

2. Wenn Sie überprüfen möchten, ob der Ordner *\Bin\\* erstellt wurde und die Anwendung *MSBuildSample* enthält, geben Sie **dir Bin** ein.

3. Testen Sie die Anwendung, indem Sie **Bin\MSBuildSample** eingeben.

     Die Meldung **Hello, world!** sollte angezeigt werden.

## <a name="add-build-targets"></a>Hinzufügen von Buildzielen

 Fügen Sie der Projektdatei anschließend wie folgt zwei weitere Ziele hinzu:

- Ein Clean-Ziel, mit dem alte Dateien gelöscht werden.

- Ein Rebuild-Ziel, das über das `DependsOnTargets`-Attribut die Ausführung der Clean-Aufgabe erzwingt, bevor die Build-Aufgabe ausgeführt wird.

Da Sie nun über mehrere Ziele verfügen, können Sie das Build-Ziel als Standardziel festlegen.

### <a name="to-add-build-targets"></a>So fügen Sie Build-Ziele hinzu

1. Fügen Sie in der Projektdatei direkt nach dem Build-Ziel die folgenden beiden Ziele hinzu:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Das Clean-Ziel ruft die Delete-Aufgabe auf, die Anwendung zu löschen. Das Rebuild-Ziel wird erst ausgeführt, nachdem das Clean-Ziel und das Build-Ziel ausgeführt wurden. Zwar weist das Rebuild-Ziel keine Aufgaben auf, doch führt es dazu, dass das Clean-Ziel vor dem Build-Ziel ausgeführt wird.

2. Fügen Sie dem ersten `DefaultTargets`-Element das folgende `Project`-Attribut hinzu:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Damit wird das Build-Ziel als Standardziel festgelegt.

Die Projektdatei sollte nun dem folgenden Code ähneln:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Testen der Buildziele

 Mit den neuen Build-Zielen können Sie die folgenden Funktionen der Projektdatei testen:

- Erstellen des Standardbuilds

- Festlegen des Anwendungsnamens an der Eingabeaufforderung

- Löschen der Anwendung, bevor eine andere Anwendung erstellt wird

- Löschen der Anwendung, ohne eine andere Anwendung zu erstellen

### <a name="to-test-the-build-targets"></a>So testen Sie die Build-Ziele

1. Geben Sie an der Eingabeaufforderung **msbuild helloworld.csproj -p:AssemblyName=Greetings** ein.

     Da Sie das Ziel nicht explizit mit dem Schalter **-t** festgelegt haben, führt MSBuild das Build-Standardziel aus. Der Schalter **-p** überschreibt die Eigenschaft `AssemblyName` und gibt dieser den neuen Wert `Greetings`. Dies führt zum Erstellen der neuen Anwendung *Greetings.exe* im Ordner *\Bin\\* .

2. Wenn Sie überprüfen möchten, ob der Ordner *\Bin\\* die Anwendung *MSBuildSample* und die neue Anwendung *Greetings* enthält, geben Sie **dir Bin** ein.

3. Testen Sie die Anwendung Greetings, indem Sie **Bin\Greetings** eingeben.

     Die Meldung **Hello, world!** sollte angezeigt werden.

4. Löschen Sie die Anwendung MSBuildSample, indem Sie **msbuild helloworld.csproj -t:clean** eingeben.

     Dadurch wird die Clean-Aufgabe ausgeführt, um die Anwendung mit dem `AssemblyName`-Standardeigenschaftswert `MSBuildSample` zu entfernen.

5. Löschen Sie die Anwendung Greetings, indem Sie **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings** eingeben.

     Dadurch wird die Clean-Aufgabe ausgeführt, um die Anwendung mit dem angegebenen **AssemblyName**-Eigenschaftswert `Greetings` zu entfernen.

6. Wenn Sie überprüfen möchten, ob der Ordner *\Bin\\* jetzt leer ist, geben Sie **dir Bin** ein.

7. Typ **msbuild**.

     Zwar ist keine Projektdatei angegeben, doch erstellt MSBuild die Datei *helloworld.csproj*, da der aktuelle Ordner nur eine Projektdatei enthält. Auf diese Weise wird die Anwendung *MSBuildSample* im Ordner *\Bin\\* erstellt.

     Wenn Sie überprüfen möchten, ob der Ordner *\Bin\\* die Anwendung *MSBuildSample* enthält, geben Sie **dir Bin** ein.

## <a name="build-incrementally"></a>Inkrementelles Erstellen

 Sie können MSBuild anweisen, ein Ziel nur zu erstellen, wenn die Quelldateien oder Zieldateien, von denen das Ziel abhängig ist, geändert wurden. MSBuild bestimmt anhand des Zeitstempels einer Datei, ob diese geändert wurde.

### <a name="to-build-incrementally"></a>So nehmen Sie einen inkrementellen Build vor

1. Fügen Sie in der Projektdatei dem ersten Build-Ziel die folgenden Attribute hinzu:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Damit wird festgelegt, dass das Build-Ziel von den in der `Compile`-Elementgruppe angegebenen Eingabedateien abhängt und dass als Ausgabeziel die Anwendungsdatei verwendet wird.

     Das resultierende Build-Ziel sollte dem folgenden Code ähneln:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Testen Sie das Build-Ziel, indem Sie an der Eingabeaufforderung **msbuild -v:d** eingeben.

     Vergessen Sie nicht, dass *helloworld.csproj* die Standardprojektdatei und „Build“ das Standardziel darstellt.

     Mit dem Schalter **-v:d** wird eine ausführliche Beschreibung für den Buildprozess angegeben.

     Die folgenden Zeilen sollten angezeigt werden:

     **Das Ziel „Build“ wird übersprungen, da alle Ausgabedateien hinsichtlich der Eingabedateien aktuell sind.**

     **en: HelloWorld.cs**

     **Ausgabedateien: BinMSBuildSample.exe**

     MSBuild überspringt das Build-Ziel, da seit dem letzten Build der Anwendung keine der Quelldateien geändert wurde.

## <a name="c-example"></a>Beispiel für C#

Das folgende Beispiel enthält eine Projektdatei, durch die eine C#-Anwendung kompiliert und eine Meldung mit dem Namen der Ausgabedatei protokolliert wird.

### <a name="code"></a>Code

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Beispiel für Visual Basic

Das folgende Beispiel enthält eine Projektdatei, durch die eine Visual Basic-Anwendung kompiliert und eine Meldung mit dem Namen der Ausgabedatei protokolliert wird.

### <a name="code"></a>Code

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Ausblick

 Visual Studio kann einen großen Teil der in dieser exemplarischen Vorgehensweise gezeigten Aktionen automatisch übernehmen. Informationen zum Erstellen und Bearbeiten sowie zum Build und zu Tests von MSBuild-Projektdateien in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über MSBuild](../msbuild/msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
