---
title: Erweitern des Buildprozesses
description: Erfahren Sie mehr über verschiedene Möglichkeiten, um den Buildprozess so zu ändern, dass Sie den Vorgang zum Erstellen Ihrer Projekte steuern und anpassen können.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07f0312892d9f4f4073cf6fb2c9537ffa52a6267
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436350"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Vorgehensweise: Erweitern des Visual Studio-Buildprozesses

Der Visual Studio-Buildprozess wird durch eine Reihe von MSBuild- *TARGETS* -Dateien definiert, die in die Projektdatei importiert werden. Eine dieser importierten Dateien ( *Microsoft.Common.targets* ) kann erweitert werden, um Ihnen das Ausführen benutzerdefinierter Aufgaben in unterschiedlichen Phasen während des Buildprozesses zu ermöglichen. In diesem Artikel werden die zwei Methoden erläutert, mit denen der Visual Studio-Buildprozess erweitert werden kann:

- Überschreiben spezifischer vordefinierter Ziele, die in den allgemeinen Zielen definiert werden ( *Microsoft.Common.targets* oder die importierten Dateien)

- Überschreiben der DependsOn-Eigenschaften, die in den allgemeinen Zielen definiert werden

## <a name="override-predefined-targets"></a>Überschreiben vordefinierter Ziele

Die allgemeinen Ziele enthalten vordefinierte, leere Ziele, die vor und nach einigen der wichtigen Ziele im Buildprozess aufgerufen werden. Beispielsweise ruft MSBuild das `BeforeBuild`-Ziel vor dem `CoreBuild`-Hauptziel und das `AfterBuild`-Ziel nach dem `CoreBuild`-Ziel auf. Die leeren Ziele in den allgemeinen Zielen führen standardmäßig keine Aktionen aus. Sie können aber ihr Standardverhalten überschreiben, indem Sie die Ziele definieren, die in einer Projektdatei enthalten sein sollen, die allgemeine Ziele importiert. Durch das Überschreiben der vordefinierten Ziele können Sie den Buildprozess mit MSBuild-Aufgaben besser steuern.

> [!NOTE]
> Projekte im Format von SDKs importieren Ziele implizit *nach der letzten Codezeile der Projektdatei* . Das heißt, Sie können die Standardziele nicht überschreiben, es sei denn, Sie legen Ihre Importe wie unter [Vorgehensweise: Verwenden von SDKs für MSBuild-Projekte](how-to-use-project-sdk.md) beschrieben manuell fest.

#### <a name="to-override-a-predefined-target"></a>So überschreiben Sie ein vordefiniertes Ziel

1. Identifizieren Sie ein vordefiniertes Ziel in den allgemeinen Zielen, das Sie überschreiben möchten. In der Tabelle unten finden Sie die vollständige Liste der Ziele, die Sie bedenkenlos überschreiben können.

2. Definieren Sie das Ziel bzw. die Ziele am Ende der Projektdatei, unmittelbar vor dem `</Project>`-Tag. Beispiel:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Erstellen Sie die Projektdatei.

In der folgenden Tabelle werden alle Ziele in den allgemeinen Zielen aufgeführt, die Sie bedenkenlos überschreiben können.

|Zielname|BESCHREIBUNG|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden vor oder nach Abschluss der Kompilierung ausgeführt. Die meisten Anpassungen werden in einem dieser beiden Ziele ausgeführt.|
|`BeforeBuild`, `AfterBuild`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem alles Weitere erstellt wurde. **Hinweis:** Die Ziele `BeforeBuild` und `AfterBuild` wurden bereits in Kommentaren am Ende der meisten Projektdateien definiert. Dadurch können Sie ohne großen Aufwand Pre- und Postbuildereignisse zu Ihrer Projektdatei hinzufügen.|
|`BeforeRebuild`, `AfterRebuild`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Neuerstellen von Kernen aufgerufen wurde. Die Reihenfolge der Ausführung der Ziele in *Microsoft.Common.targets* lautet wie folgt: `BeforeRebuild`, `Clean`, `Build` und anschließend `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Löschen von Kernen aufgerufen wurde.|
|`BeforePublish`, `AfterPublish`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Funktion zum Veröffentlichen von Kernen aufgerufen wurde.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem die Assemblyverweise aufgelöst wurden.|
|`BeforeResGen`, `AfterResGen`|Aufgaben, die in eines dieser Ziele eingefügt wurden, werden ausgeführt, bevor oder nachdem Ressourcen generiert wurden.|

## <a name="example-aftertargets-and-beforetargets"></a>Beispiel: „AfterTargets“ und „BeforeTargets“

Im folgenden Beispiel sehen Sie, wie Sie mit dem `AfterTargets`-Attribut ein benutzerdefiniertes Ziel hinzufügen, das eine Aktion für die Ausgabedateien ausführt. In diesem Beispiel werden die Ausgabedateien in den neuen Ordner *CustomOutput* kopiert.  Im Beispiel wird auch veranschaulicht, wie die vom benutzerdefinierten Buildvorgang mit einem `CustomClean`-Ziel erstellten Dateien bereinigt werden, indem das `BeforeTargets`-Attribut verwendet und angegeben wird, dass der benutzerdefinierte Bereinigungsvorgang vor dem `CoreClean`-Ziel ausgeführt wird.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Verwenden Sie dabei unbedingt andere Namen als die in der Tabelle des vorherigen Abschnitts aufgelisteten vordefinierten Ziele (das benutzerdefinierte Buildziel wurde hier beispielsweise `CustomAfterBuild` und nicht `AfterBuild` genannt). Das liegt daran, dass die vordefinierten Ziele vom SDK-Import überschrieben werden, der sie auch definiert. Der Import der Zieldatei, die diese Ziele überschreibt, wird nicht angezeigt. Die Datei wird jedoch implizit am Ende der Projektdatei hinzugefügt, wenn Sie die Methode des `Sdk`-Attributs zum Verweisen auf ein SDK verwenden.

## <a name="override-dependson-properties"></a>Überschreiben von DependsOn-Eigenschaften

Mit dem Überschreiben von vordefinierten Zielen lässt sich der Buildprozess leicht erweitern. Da MSBuild die Definition von Zielen aber nacheinander auswertet, können Sie ein anderes Projekt, das Ihr Projekt importiert, nicht daran hindern, die bereits überschriebenen Ziele noch einmal zu überschreiben. Das letzte in der Projektdatei definierte `AfterBuild`-Ziel wird z.B. während des Buildprozesses verwendet, nachdem alle anderen Projekte importiert wurden.

Sie können sich vor dem unbeabsichtigten Überschreiben von Zielen schützen, indem Sie die DependsOn-Eigenschaften überschreiben, die in den `DependsOnTargets`-Attributen der allgemeinen Ziele verwendet werden. So enthält das `Build`-Ziel z.B. einen `DependsOnTargets`-Attributwert von `"$(BuildDependsOn)"`. Zu berücksichtigen:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Dieser XML-Codeausschnitt gibt an, dass vor der Ausführung des `Build`-Ziels alle in der `BuildDependsOn`-Eigenschaft angegebenen Ziele zuerst ausgeführt werden müssen. Die `BuildDependsOn`-Eigenschaft ist definiert als:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Sie können diesen Eigenschaftswert überschreiben, indem Sie eine andere Eigenschaft mit dem Namen `BuildDependsOn` am Ende der Projektdatei deklarieren. Durch Einschließen der vorherigen `BuildDependsOn`-Eigenschaft in die neue Eigenschaft können Sie neue Ziele am Anfang und Ende der Zielliste hinzufügen. Beispiel:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Projekte, in die Ihre Projektdateien importiert werden, können diese Eigenschaften überschreiben, ohne die von Ihnen vorgenommenen Anpassungen zu überschreiben.

#### <a name="to-override-a-dependson-property"></a>So überschreiben Sie eine DependsOn-Eigenschaft

1. Identifizieren Sie eine vordefinierte DependsOn-Eigenschaft in den allgemeinen Zielen, die Sie überschreiben möchten. In der folgenden Tabelle finden Sie eine Liste der Eigenschaften der häufig überschriebenen DependsOn-Eigenschaften.

2. Definieren Sie eine andere Instanz der Eigenschaft oder Eigenschaften am Ende der Projektdatei. Schließen Sie die ursprüngliche Eigenschaft, z.B. `$(BuildDependsOn)`, in die neue Eigenschaft ein.

3. Definieren Sie Ihre benutzerdefinierten Ziele vor oder nach der Eigenschaftsdefinition.

4. Erstellen Sie die Projektdatei.

### <a name="commonly-overridden-dependson-properties"></a>Häufig überschriebene DependsOn-Eigenschaften

|Eigenschaftenname|BESCHREIBUNG|
|-------------------|-----------------|
|`BuildDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie benutzerdefinierte Ziele vor oder nach dem gesamten Buildprozess einfügen möchten|
|`CleanDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie die Ausgabe Ihres benutzerdefinierten Buildprozesses bereinigen möchten|
|`CompileDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie benutzerdefinierte Prozesse vor oder nach dem Kompilieren einfügen möchten|

## <a name="example-builddependson-and-cleandependson"></a>Beispiel: „BuildDependsOn“ und „CleanDependsOn“

Das folgende Beispiel ähnelt in vielerlei Hinsicht dem Beispiel `BeforeTargets` und `AfterTargets`, zeigt jedoch, wie eine ähnliche Funktionalität erzielt werden kann. Es wird der Build erweitert, indem mithilfe von `BuildDependsOn` Ihre eigene `CustomAfterBuild`-Aufgabe hinzugefügt wird, die die Ausgabedateien nach dem Buildvorgang kopiert. Zudem wird mithilfe von `CleanDependsOn` die entsprechende `CustomClean`-Aufgabe hinzugefügt.  

In diesem Beispiel handelt es sich um ein Projekt im SDK-Format. Wie bereits weiter oben in diesem Artikel im Hinweis zu Projekten im SDK-Format erwähnt, müssen Sie die manuelle Importmethode anstelle des `Sdk`-Attributs verwenden, das in Visual Studio für das Generieren von Projektdateien verwendet wird.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

Die Reihenfolge der Elemente spielt eine wichtige Rolle. Die Elemente `BuildDependsOn` und `CleanDependsOn` müssen nach dem Import der Standarddatei für SDK-Ziele angezeigt werden.

## <a name="see-also"></a>Weitere Informationen

- [Integration von Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [TARGETS-Dateien](../msbuild/msbuild-dot-targets-files.md)
