---
title: CombinePath-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „CombinePath“ verwenden, um die angegebenen Pfade zu einem einzigen Pfad zu kombinieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1eb27a311f1b61e3e36b4c9eaa65de7f3fd8f1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939499"
---
# <a name="combinepath-task"></a>CombinePath-Aufgabe

Kombiniert die angegebenen Pfade zu einem einzigen Pfad.
## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der [CombinePath-Aufgabe](../msbuild/combinepath-task.md) beschrieben.


|Parameter|Beschreibung|
|---------------|-----------------|
|`BasePath`|Erforderlicher `String` -Parameter.<br /><br /> Der Basispfad, der mit den anderen Pfaden kombiniert werden soll. Der Pfad kann relativ, absolut oder nicht angegeben sein.|
|`Paths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Eine Liste einzelner Pfade, die mit BasePath zu einem kombinierten Pfad kombiniert werden können. Pfade können relativ oder absolut sein.|
|`CombinedPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Der kombinierte Pfad, der durch diese Aufgabe erstellt wurde|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

 Das folgende Beispiel zeigt, wie eine Ausgabeordnerstruktur mit `CombinePath` erstellt wird, um die Eigenschaft `$(OutputDirectory)` zu konstruieren, indem der mit `$(ReleaseDirectory)` verknüpfte Stammpfad `$(PublishRoot)` mit der Unterordnerliste `$(LangDirectories)` kombiniert wird.

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

Die einzige Eigenschaft, der `CombinePath` erlaubt, eine Liste zu sein, ist `Paths`. In diesem Fall ist die Ausgabe ebenfalls eine Liste. Wenn also `$(PublishRoot)` gleich *C:\Site1\\* ist, `$(ReleaseDirectory)` gleich *Release\\* ist, und `@(LangDirectories)` gleich *en-us\;fr-fr\\* ist, dann erstellt dieses Beispiel die folgenden Ordner:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
