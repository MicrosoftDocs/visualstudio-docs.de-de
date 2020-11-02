---
title: Verweisen auf den Namen oder Speicherort der Projektdatei
description: Erfahren Sie, wie Sie reservierte Eigenschaften in MSBuild verwenden, um auf einen Projektdateinamen oder Speicherort zu verweisen, ohne eigene Eigenschaften erstellen zu müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccc356e1859f447db1ac18a437b8fc2317925b0f
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436348"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei

Sie können den Namen oder Speicherort des Projekts in der Projektdatei verwenden, selbst ohne eine eigene Eigenschaft erstellt zu haben. MSBuild stellt reservierte Eigenschaften zur Verfügung, die auf die Projektdateinamen sowie andere Eigenschaften verweisen, die zum Projekt gehören. Weitere Informationen zu reservierten Eigenschaften finden Sie unter [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Verwenden der Projekteigenschaften

 MSBuild stellt einige reservierte Eigenschaften bereit, die Sie in den Projektdateien verwenden können, ohne diese jedes Mal zu definieren. Beispiel: Die reservierte Eigenschaft `MSBuildProjectName` stellt einen Verweis zum Projektdateinamen bereit. Die reservierte Eigenschaft `MSBuildProjectDirectory` stellt einen Verweis zum Speicherort der Projektdatei bereit.

#### <a name="to-use-the-project-properties"></a>So verwenden Sie die Projekteigenschaften

- Verweisen Sie die Eigenschaft in der Projektdatei mit der $()-Notation genau so, wie Sie es mit anderen Eigenschaften machen würden. Beispiel:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Ein Vorteil der Verwendung einer reservierten Eigenschaft ist, dass alle Änderungen am Projektdateinamen automatisch integriert sind. Das nächste Mal, wenn Sie das Projekt erstellen, wird die Ausgabedatei den neuen Namen haben, ohne dass von Ihnen Handlungsbedarf besteht.

  Weitere Informationen zur Verwendung von Sonderzeichen in Datei- oder Projektverweisen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Reservierte Eigenschaften können nicht in der Projektdatei neu definiert werden.

## <a name="example-1"></a>Beispiel 1

 Die folgende Beispiel-Projektdatei verweist den Projektnamen als reservierte Eigenschaft, um den Namen für die Ausgabe anzugeben.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Beispiel 2

 Die folgende Beispielprojektdatei verwendet die reservierte Eigenschaft `MSBuildProjectDirectory`, um den vollständigen Pfad zu einer Datei im Speicherort der Projektdatei zu erstellen.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Das Beispiel verwendet die Syntax der [Eigenschaftenfunktion](property-functions.md), um die statische .NET Framework-Methode <xref:System.IO.Path.Combine*?displayProperty=fullName> aufzurufen.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
- [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
