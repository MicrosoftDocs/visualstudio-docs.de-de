---
title: Verweisen auf den Namen oder Speicherort der Projektdatei
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
ms.openlocfilehash: 29960de09b512a419a56a61f493702485c287475
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036456"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei

Sie können den Namen oder Speicherort des Projekts in der Projektdatei verwenden, selbst ohne eine eigene Eigenschaft erstellt zu haben. MSBuild stellt reservierte Eigenschaften zur Verfügung, die auf die Projektdateinamen sowie andere Eigenschaften verweisen, die zum Projekt gehören. Weitere Informationen zu reservierten Eigenschaften finden Sie unter [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Verwenden der Projekteigenschaften

 MSBuild stellt einige reservierte Eigenschaften bereit, die Sie in den Projektdateien verwenden können, ohne diese jedes Mal zu definieren. Beispiel: Die reservierte Eigenschaft `MSBuildProjectName` stellt einen Verweis zum Projektdateinamen bereit. Die reservierte Eigenschaft `MSBuildProjectDirectory` stellt einen Verweis zum Speicherort der Projektdatei bereit.

#### <a name="to-use-the-project-properties"></a>So verwenden Sie die Projekteigenschaften

- Verweisen Sie die Eigenschaft in der Projektdatei mit der $()-Notation genau so, wie Sie es mit anderen Eigenschaften machen würden. Zum Beispiel:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Ein Vorteil der Verwendung einer reservierten Eigenschaft ist, dass alle Änderungen am Projektdateinamen automatisch integriert sind. Das nächste Mal, wenn Sie das Projekt erstellen, wird die Ausgabedatei den neuen Namen haben, ohne dass von Ihnen Handlungsbedarf besteht.

  Weitere Informationen zur Verwendung von Sonderzeichen in Datei- oder Projektverweisen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Reservierte Eigenschaften können nicht in der Projektdatei neu definiert werden.

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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

## <a name="see-also"></a>Siehe auch

- [MSBuild](../msbuild/msbuild.md)
- [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
