---
title: Erstellen identischer Quelldateien mit unterschiedlichen Optionen
description: Erfahren Sie, wie Sie unterschiedliche MSBuild-Buildkonfigurationen erstellen, um dieselben Quelldateien mit unterschiedlichen Optionen zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd9d77e32f9c287ac2dfcf3905fe9335e119a3a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914498"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Vorgehensweise: Erstellen identischer Quelldateien mit unterschiedlichen Optionen

Wenn Sie Projekte erstellen, kompilieren Sie häufig die gleichen Komponenten mit unterschiedlichen Buildoptionen. So können Sie, z.B. ein Debugbuild mit Symbolinformationen oder ein Releasebuild ohne Symbolversionen, aber mit aktivierten Optimierungen erstellen. Alternativ können Sie ein Projekt erstellen, das auf einer bestimmten Plattform wie x86 oder x64 ausgeführt wird. In allen diesen Fällen bleiben die meisten Buildoptionen gleich. Nur ein paar Optionen werden zur Steuerung der Buildkonfiguration geändert. Sie verwenden Eigenschaften und Bedingungen mit MSBuild, um die unterschiedlichen Buildkonfigurationen zu erstellen.

## <a name="use-properties-to-control-build-settings"></a>Verwenden von Eigenschaften zum Steuern von Buildeinstellungen

Das Element `Property` definiert eine Variable, die in einer Projektdatei, z.B. den Speicherort eines temporären Ordners, mehrmals verwiesen wird oder um die Werte für Eigenschaften festzulegen, die in mehrere Konfigurationen (z.B. einem Debug- oder Releasebuild) verwendet werden. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild Properties (MSBuild-Eigenschaften)](../msbuild/msbuild-properties.md).

Sie können Eigenschaften verwenden, um die Konfiguration Ihres Builds zu ändern, ohne die Projektdatei zu ändern. Das Attribut `Condition` des Elements `Property` und `PropertyGroup` hilft Ihnen beim Ändern der Eigenschaftenwerte. Weitere Informationen zu MSBuild-Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>So legen Sie eine Eigenschaftengruppe fest, die von einer anderen Eigenschaft abhängt

- Verwenden Sie ein Attribut `Condition` im Element `PropertyGroup`, das ähnlich dem Folgenden ist:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>So definieren Sie eine Eigenschaft, die von einer anderen Eigenschaft abhängt

- Verwenden Sie ein Attribut `Condition` im Element `Property`, das ähnlich dem Folgenden ist:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Festlegen von Eigenschaften in der Befehlszeile

Nachdem die Projektdatei geschrieben wurde und mehrere Konfigurationen zulässt, müssen Sie die Möglichkeit haben, diese Konfigurationen zu ändern, wenn Sie Ihr Projekt erstellen. MSBuild bietet diese Möglichkeit, indem es ermöglicht wird, Eigenschaften mithilfe des Schalters **-property** oder **-p** in der Befehlszeile anzugeben.

### <a name="to-set-a-project-property-at-the-command-line"></a>So legen Sie eine Projekteigenschaft in der Befehlszeile fest

- Verwenden Sie den Schalter **-property** mit der Eigenschaft und dem Eigenschaftswert. Beispiel:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  oder

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>So geben Sie mehr als eine Projekteigenschaft in der Befehlszeile an

- Verwenden Sie mehrmals den Schalter **-property** oder **-p** mit der Eigenschaft und den Eigenschaftswerten, oder verwenden Sie einen Schalter **-property** bzw. **-p** und unterteilen mehrere Eigenschaft mithilfe von Semikolons (;). Beispiel:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  oder

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Umgebungsvariablen werden ebenfalls als Eigenschaften behandelt und automatisch von MSBuild integriert. Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie unter [Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Der Wert der Eigenschaft, die in der Befehlszeile angegeben ist, hat Vorrang vor jedem Wert, dem in der Projektdatei der gleiche Wert zugewiesen wurde. Dieser Wert hat Vorrang vor dem Wert in einer Umgebungsvariable.

  Sie können dieses Verhalten ändern, indem Sie das Attribut `TreatAsLocalProperty` in einem Projekttag verwenden. Der Eigenschaftswert, der auf der Befehlszeile angegeben wurde, hat für Eigenschaftsnamen, die mit diesem Attribut aufgeführt sind, kein Vorrang vor dem Wert in der Projektdatei. Sie finden ein Beispiel weiter unten in diesem Thema.

## <a name="example-1"></a>Beispiel 1

Das folgende Codebeispiel, das Projekt „Hello World“, enthält zwei neue Eigenschaftengruppen, die verwendet werden können, um ein Debugbuild und ein Releasebuild zu erstellen.

So erstellen Sie die Debugversion des Projekts:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

So erstellen Sie die Verkaufsversion des Projekts:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Beispiel 2

Das folgende Beispiel veranschaulicht, wie das `TreatAsLocalProperty`-Attribut verwendet wird. Die Eigenschaft `Color` hat den Wert `Blue` in der Projektdatei und `Green` in der Befehlszeile. Mit `TreatAsLocalProperty="Color"` im Projekttag setzt die Befehlszeileneigenschaft (`Green`) nicht die Eigenschaft außer Kraft, die in der Projektdatei definiert ist (`Blue`).

Geben Sie zum Erstellen des Projekts den folgenden Befehl ein:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)
