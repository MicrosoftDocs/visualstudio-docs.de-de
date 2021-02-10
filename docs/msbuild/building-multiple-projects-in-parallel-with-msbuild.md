---
title: Paralleles Erstellen von mehreren Projekten mit MSBuild | Microsoft-Dokumentation
description: Erfahren Sie mehr über die MSBuild-Einstellungen, mit denen Sie durch eine parallele Ausführung schneller mehrere Projekte erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8e90a649a11933e4281140299bf9ee1b564a212
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939629"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>Paralleles Erstellen von mehreren Projekten mit MSBuild

Sie können MSBuild verwenden, um mehrere Projekte schneller zu erstellen, indem Sie sie parallel ausführen. Um Builds parallel auszuführen, verwenden Sie die folgenden Einstellungen auf einem Mehrkern- oder Mehrprozessorcomputer:

- den Schalter `-maxcpucount` in einer Eingabeaufforderung

- den <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>-Aufgabenparameter in einer MSBuild-Aufgabe

> [!NOTE]
> Der Schalter **-verbosity** (**-v**) in einer Befehlszeile kann die Buildleistung ebenfalls beeinflussen. Die Buildleistung verringert sich möglicherweise, wenn die Ausführlichkeit der Buildprotokollinformationen auf die Einstellung "Detailliert" oder "Diagnose" festgelegt ist, die beide für die Problembehandlung verwendet werden. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) und [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

## <a name="-maxcpucount-switch"></a>-maxcpucount-Schalter

Wenn Sie den Schalter `-maxcpucount` oder die kurze Form `-m` verwenden, kann MSBuild die angegebene Anzahl von *MSBuild.exe*-Prozessen erstellen, die parallel ausgeführt werden können. Diese Prozesse werden auch als "Arbeitsprozesse" bezeichnet. Jeder Arbeitsprozess verwendet einen anderen Kern oder Prozessor, soweit verfügbar, um ein Projekt zu der gleichen Zeit zu erstellen wie andere verfügbare Prozessoren. Wenn Sie zum Beispiel diesen Schalter auf den Wert "4" festlegen, erstellt MSBuild vier Arbeitsprozesse zum Erstellen des Projekts.

Wenn Sie den Schalter `-maxcpucount` verwenden, ohne einen Wert anzugeben, verwendet MSBuild alle Prozessoren des Computers.

Weitere Informationen über diesen Schalter, der in MSBuild 3.5 eingeführt wurde, finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

Das folgende Beispiel weist MSBuild an, drei Arbeitsprozesse zu verwenden. Wenn Sie diese Konfiguration verwenden, kann MSBuild drei Projekte gleichzeitig erstellen.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>Aufgabenparameter „BuildInParallel“

`BuildInParallel` ist ein optionaler boolescher Parameter für eine MSBuild-Aufgabe. Wenn `BuildInParallel` auf `true` (der Standardwert ist `true`) festgelegt ist, werden mehrere Arbeitsprozesse zum gleichzeitigen Erstellen so vieler Projekte wie möglich erzeugt. Damit dies ordnungsgemäß funktioniert, muss der `-maxcpucount`-Schalter auf einen Wert größer 1 festgelegt sein, und das System muss mindestens ein Dualcore-System sein oder über mindestens zwei Prozessoren verfügen.

Nachfolgend ist ein Beispiel aus *microsoft.common.targets* aufgeführt, das veranschaulicht, wie der `BuildInParallel`-Parameter festgelegt wird.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>Weitere Informationen:

- [Verwenden mehrerer Prozessoren für die Erstellung von Projekten](../msbuild/using-multiple-processors-to-build-projects.md)
- [Schreiben von multiprozessorfähigen Protokollierungen](../msbuild/writing-multi-processor-aware-loggers.md)
- [Blog zum Optimieren der C++-Buildparallelität](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
